var net = require("net");

var port = 6667;
var host = "irc.inserthosthere.com";
var nick = "Test";
var user ="Testing";
var room ="#lobby";

var client = net.createConnection(port, host);
client.setEncoding('utf-8');


client.addListener('connect', function () {
	console.log("connecting...");
	client.write('NICK '+nick+'\r\n', 'binary'); //Binary for nick multi language support
	client.write('USER ' + user + ' 0 * :' + user + '\r\n');
});

client.on('data', function (message) {
	console.log(message);
	if ( message.match( /^PING.*/ ) ) {
			client.write( 'PONG ' + message.split(' ')[1] + '\r\n' );
		}
			
	}
});

client.on('error', function (err) {
	console.log(err);
});

client.on('end', function (message) {
	console.log(message);
});
