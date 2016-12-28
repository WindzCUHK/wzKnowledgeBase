## D3.js
[D3.js 101](https://www.dashingd3js.com/table-of-contents)

# nodemailer
```js
var nodemailer = require('nodemailer');

var sendUser = '';
var sendPw = '';
var fromEmail = '';
var toEmail = '';

var transporter = nodemailer.createTransport({
    host: '192.168.1.123', // hostname
    port: 587, // port for secure SMTP
    auth: {
        user: sendUser,
        pass: sendPw
    },
    // tls: { rejectUnauthorized: true },
    // ignoreTLS: true,
    // secureConnection: false, // TLS requires secureConnection to be false

    debug: true,
    logger: true
});

transporter.verify(function(error, success) {
    if (error) {
        console.log(error);
    } else {
        console.log('Server is ready to take our messages');

        transporter.sendMail({
            from: fromEmail,
            to: toEmail,
            subject: 'hello world!',
            text: 'hi mail'
        }, function(error, response) {
            if (error) {
                console.log(error);
            } else {
                console.log('Message sent');
            }
        });
    }
});
```

# couchbase
```js
const couchbase = require('couchbase');

const cluster = new couchbase.Cluster('couchbase://192.168.1.123');
const bucket = cluster.openBucket('user', 'pw');

const bm = bucket.manager();

// bm.getDesignDocument('dev_views', function(err, result) {
//  console.dir(result.views);
// });

const mapFunctionString = 'function(doc, meta) {}';
const reduceFunctionString = 'function(key, values, rereduce) {}';

bm.upsertDesignDocument('dev_test_view_doc', {
    views: {
        test_view: {
            map: mapFunctionString,
            reduce: reduceFunctionString
        }
    }
}, function (err, isSuccess) {
    console.log('upsert design doc', isSuccess);
});
```
