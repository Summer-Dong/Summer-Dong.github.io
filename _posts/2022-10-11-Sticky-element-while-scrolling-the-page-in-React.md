---
layout: post
title: Sticky element while scrolling the page in React
date: 2022-10-11 19:20:23 +0900
category: javascript
---
### 使用场景：页面中存在某一元素，当滑动滚轴使得此元素不能被看到时，想使这个元素一直被固定在页面顶部，而滚动滚轴使得此元素原来所在位置又出现时，使此元素回归原来位置
```tsx
import React, { useEffect, useRef, useState } from 'react'
import styled from 'styled-components'

export default ({ children, classes }): JSX.Element => {
    const stickyEle = useRef()
    const [eleY, setEleY] = useState<number>(0)
    const [isScrolledOver, setIsScrolledOver] = useState(false)
    const StyledStickyEle = styled.div`
        &.fixed {
            position: fixed;
            left: 0;
            right: 0;
            top: 0;
            z-index: 999;
            padding: 1.5rem 5.5rem !important; // custom css
            background-color: #edeff1; // custom css
        }
    `

    const onScroll = () => {
        !!eleY && setIsScrolledOver(window.scrollY > eleY)
    }
    window.addEventListener('scroll', onScroll, { passive: true })
    useEffect(() => {
        !eleY && stickyEle.current.getBoundingClientRect().y && setEleY(stickyEle.current.getBoundingClientRect().y)
    }, [eleY])
    useEffect(() => {
        return () => window.removeEventListener('scroll', onScroll)
    })
    return (
        <StyledStickyEle ref={stickyEle} className={`${classes} ${isScrolledOver && 'fixed'}`}>
            {children}
        </StyledStickyEle>
    )
}

```
## Example:
<iframe height=500 width=500 src="https://summer-dong.github.io/public/img/sticky-element.webm" allowfullscreen> </iframe>
