# reactstudy-first

使用react实现极简易编辑器功能.

## 相关链接：

* [原生JS版本](https://jiuzilong.github.io/reactstudy-first/src/testC3.html)

* [react实现版本](https://jiuzilong.github.io/reactstudy-first/src/testC3_react.html)

* [下载地址](https://github.com/jiuzilong/reactstudy-first/archive/master.zip)

## 步骤：
1. 安装nodejs插件
```
 npm install;
```

2. 运行webpack
```
 webpack
```

3. 浏览src目录下的`testC3_react.html`


## 核心JS代码：

```javascript
    'use strict'

	import React,{Component} from 'react'
	import ReactDOM from 'react-dom'
	class TextEditor extends Component{
	  constructor(props){
	    super(props);
	    this.state = {
	      color:props.color?props.color:'gray',
	      size:props.size?props.fontSize:'14px',
	      text:props.text?props.text:""
	    }
	  }
	  handleChange(valObj){
	    this.setState(valObj);
	  }
	  render(){

	      return (
		<div>
		  <div className="fl w33 b p"><p style={{color:this.state.color,fontSize:this.state.size}}>{this.state.text}</p></div>
		  <Changer handleChange={this.handleChange.bind(this)} />
		  <Changer handleChange={this.handleChange.bind(this)} />
		</div>
	      )
	  }
	}

	class Changer extends Component{
	  getValues(){
	    var text = this.refs.content.value;
	    var size = this.refs.fontSize.value;
	    if(/^\d+(\.\d+)?$/.test(size)){
	      size = size+"px";
	    }
	    var color = this.refs.fontColor.value;
	    return {text,size,color};
	  }
	  onChange(){
	    this.props.handleChange(this.getValues());
	  }
	  onSave(){
	    alert(JSON.stringify(this.getValues()));
	  }
	  render(){
	    return (<div className="fl w33 p">
	      <p>内容：<input ref="content" onChange = {this.onChange.bind(this)} className="textInputEl" /></p>
	      <p>字号：<input ref="fontSize" onChange = {this.onChange.bind(this)} className="textInputEl" /></p>
	      <p>颜色：<input ref="fontColor" onChange = {this.onChange.bind(this)} className="textInputEl" /></p>
	      <p><button onClick = {this.onSave.bind(this)}>保存</button></p>
	    </div>
	    )
	  }
	}
	ReactDOM.render(<TextEditor />,document.getElementById("app-textEditor"));
```
