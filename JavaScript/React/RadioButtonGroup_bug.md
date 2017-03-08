# Material-UI RadioButtonGroup Bug  

The value of a radiobutton event emmited by `onChange` is one step behind the value when received from `ref.getSelectedValue()`

This bug still exists in 0.16.7, a simple delay can be used as a temporary workaround:

```javascript
<RadioButtonGroup name='type' onChange={this.handleRadioChange}>

handleRadioChange (e) {
	e.persist();
	setTimeout(() => {
		this.setState({[e.target.name]: e.target.value})
	}, 100)
}
```

[Source](https://github.com/callemall/material-ui/issues/295#issuecomment-274188464)
