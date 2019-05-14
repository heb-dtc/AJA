## Find function code in code base and update it

The function call is: `love.graphics.setColor(X, Y, W)`
The X, Y and W values should be replaced by X/255, Y/255 and W/255

```bash
grep -Rnl love.graphics.setColor | 
  xargs sed -i '/love.graphics.setColor/s/,/\/255,/g;/love.graphics.setColor/s/)/\/255)/'
```

### `sed` command breakdown

`/love.graphics.setColor/` makes sure the command only applies to text with that prefix
`s/,/\/255,/g` replaces `,` with `,/255`
`s/)/\/255)/` replaces `)` with `/255)`
