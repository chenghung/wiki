# React

React是一個由facebook開源的前端的component based library

它不是一個完整的framefork
所以不會提供像是http, form validation, i18n等之類的功能 

## Component

component通常是對應到UI上某一個區塊  
像是date picker, header, chat dialog都可能會是一個component  
它很類似我們在開發網頁時會用到一些html標籤的延伸  

例如:  
```
<DatePicker defaultTime={new Date()}/>
```

使用component的好處
- developer可以組合多個component, code的重用度更高


## Virtual DOM

Virtual DOM是React很高效的一個核心技術  
React會複製兩份Browser當前的DOM tree  
當網頁的狀態改變時(例如: call API拿到新的資料, 使用者輸入一些東西)  
React會更新其中一個DOM Copy, 並且跟另外一個DOM Copy做diff  
接者把變更的部份patch到browser的DOM tree, 這樣browser只需要重新render有變動的地方


![](https://github.com/chenghung/wiki/blob/master/programming/web/react/react-virtual-dom.png)



#### 參考資料

- [React Virtual DOM Explained in Simple English](https://programmingwithmosh.com/react/react-virtual-dom-explained/)
- [video: introduction to react virtual dom](https://www.youtube.com/watch?v=M-Aw4p0pWwg)