# React-Refs

**React Refs** are extremely important and useful in React.

Do you Remember getElementById, getElementByTagName, ...

As you remember these functions in Javascripts are used to access a Dom Node and do some code on them, As you know those are very important.


Recently, I had an issue which really annoyed me, I had a data which I mapped through it, and i need to read the input value of the checkboxes. there was approximately 400 rows in the table and there were 4 checkboxes in each row, so there were more or less 1600 checkboxes which I had to manage the state of those checkboxes. So it was a crush for me at the first.

And I knew there is a technology in React called React Refs, So React Refs solved my problem.

Example)

```js
constructor(props) {
  super(props)
  
  this.checkBoxCreate = React.createRef();
  this.checkBoxChange = React.createRef();
  this.checkBoxDelete = React.createRef();
  this.checkBoxPrint = React.createRef();
}



renderTableBodyGroupRelMenu = () => {
        if (this.props.groupRelMenuAccessGridList.loading) {
            return <tr><td>Loading...</td></tr>
        } else if (this.props.groupRelMenuAccessGridList.groupRelMenuAccessGridList?.resultBody) {

            const Body =
                <FilterResults
                    value={this.state.searchValue}
                    data={this.props.groupRelMenuAccessGridList.groupRelMenuAccessGridList.resultBody}
                    renderResults={results => (
                        results.map(el => (
                            <tr key={el.MenuId} ref={this.tableRow}>
                                <td style={{ textAlign: 'center', width: '2%' }}>ردیف</td>
                                <td style={{ textAlign: 'center', width: '45%' }}>{el.MenuId}</td>
                                <td style={{ textAlign: 'center', width: '45%' }}>{el.MenuText}</td>
                                <td style={{ textAlign: 'center', width: '2%' }}><Checkbox ref={this.checkBoxCreate} value={1} onChange={this.handleCheckBox} defaultValue={el.c}                                  defaultChecked={el.c === 1 ? true : false} /></td>
                                <td style={{ textAlign: 'center', width: '2%' }}><Checkbox ref={this.checkBoxChange} value={2} onChange={this.handleCheckBox} defaultValue={el.u}                                  defaultChecked={el.u === 1 ? true : false} /></td>
                                <td style={{ textAlign: 'center', width: '2%' }}><Checkbox ref={this.checkBoxDelete} value={3} onChange={this.handleCheckBox} defaultValue={el.d}                                  defaultChecked={el.d === 1 ? true : false} /></td>
                                <td style={{ textAlign: 'center', width: '2%' }}><Checkbox ref={this.checkBoxPrint} value={4} onChange={this.handleCheckBox} defaultValue={el.p}                                  defaultChecked={el.p === 1 ? true : false} /></td>
                            </tr>
                        )
                        )
                    )}
                />
            return Body
        }
    }
```

Then to access the Refs, first do this:

```js
console.log(this.checkBoxCreate.current) 
```

To see what paramaters there are inside it, for example in this example I need to access the value of the input tag:

So ==>>> to access the value of the input tag =>>> Then I see I have a props parameter and inside that props I have value,  so to access value:

```js
this.checkBoxPrint.current.props.value
```
