# React

React是一個由facebook open source的前端的component based library

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


#### 參考資料

- [React Virtual DOM Explained in Simple English](https://programmingwithmosh.com/react/react-virtual-dom-explained/)
- [video: introduction to react virtual dom](https://www.youtube.com/watch?v=M-Aw4p0pWwg)