#for-of

告诉jQuery对象都支持for-of语句，可以这样做：

// Since jQuery objects are array-like,
// give them the same iterator method Arrays have
jQuery.prototype[Symbol.iterator] = Array.prototype[Symbol.iterator];