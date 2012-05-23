# jQuery Infinite Scroll

A really simple & lightweight (4kb) jQuery infinite scroll plugin that's designed not to get in the way—so you can handle result fetching / updating views yourself.

## Usage

```javascript
$('#results').infiniteScroll({
	threshold: 800,
	onEnd: function() {
		console.log('No more results!');
	},
	onBottom: function(callback) {
		console.log('At the end of the page. Loading more!');
		
		// (load results & update views)
		var moreResults = true;
		
		callback(moreResults);
	}
});
```

### Options

<table>
	<tr>
		<th>Option</th>
		<th>Type</th>
		<th>Default</th>
		<th>Description</th>
	</tr>
	<tr>
		<td valign="top">threshold</td>
		<td valign="top">int</td>
		<td valign="top">500</td>
		<td valign="top">When the user scrolls to this many pixels from the bottom, `loadMore` is called.</td>
	</tr>
	<tr>
		<td valign="top">onEnd</td>
		<td valign="top">function()</td>
		<td valign="top">null</td>
		<td valign="top">Invoked when no more results are available (i.e. when <code>false</code> is passed to the callback provided to the <code>onBottom</code> method).</td>
	</tr>
	<tr>
		<td valign="top">onBottom</td>
		<td valign="top">function(callback)</td>
		<td valign="top">null</td>
		<td valign="top"><strong>(required)</strong> Invoked when the user reaches the end of the page. When you're done loading more results / updating views, invoke callback() with one argument: a bool representing whether there are more results available. If no arguments are provided, the plugin assumes there are more results.</td>
	</tr>
</table>

### Reset

If you need to reset the infinite scrolling mechanism (like if the user switches search criteria, section, whatever), simply call `$('#results').infiniteScroll('reset');`.