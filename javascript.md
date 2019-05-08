# Quick snippets
## Clean your whole Trakt Watchlist
There is no way to do this manually unless you want to click each item your self, but with the help of programming we can do this automagically.

1. Open your watchlist on Trakt and click the MANAGE button.
2. Right click anywhere and let your browser inspect
3. In the Console section of the Development Tools run the script below:

Copy paste all this to DELETE all items on the watchlist.
```javascript
$("#sortable-grid .list-edit .icons .delete").each(function(){
   $(this).click();
});
```

#### Steps Explained

This will find all the DELETE buttons
```javascript
$("#sortable-grid .list-edit .icons .delete")
```
The each function will iterate all items on a list/array
```javascript
.each(function(){
   // DO STUFF
});
```

This will click it for you...
```javascript
   $(this).click();
```

## Something else...
