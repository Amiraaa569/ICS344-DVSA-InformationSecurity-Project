Lesson 9: Vulnerable Dependencies
Before
const serialize = require('node-serialize');

exports.handler = (event, context, callback) => {
    var req = serialize.unserialize(event.body);
    var headers = serialize.unserialize(event.headers);
}
After
exports.handler = (event, context, callback) => {
    var req = JSON.parse(event.body);
    var headers = event.headers;
}
Specific changes made:
Removed: const serialize = require('node-serialize');
Changed: serialize.unserialize(event.body) → JSON.parse(event.body)
Changed: serialize.unserialize(event.headers) → event.headers
