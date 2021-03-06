# ATTED-II Displayer

This application displays data fetched from the ATTED-II web service (http://atted.jp/).

## Usage

Include "atted-displayer.js" in the head of your HTML document and create a container where the displayer will be rendered. Then instantiate the displayer like so:

```javascript
// Options for the displayer
let opts =
{                
    target: '#displayercontainer', // The target HTML element to render the table.
    AGIcode: 'At5g54270', // The search gene
    cutoff: 20, // The default cutoff / threshold
    service: "https://bar.utoronto.ca/thalemine/service", // The InterMine web service to resolve IDs
    atted: "https://bar.utoronto.ca/api/proxy/atted_api4", // The ATTED API URL
}

// Callback function to be run after a query has completed.
let callback = function(values) {
	console.log("Resolved genes from InterMine", values);
}

// A hook function to be called before a query starts.
// (Useful for clearing or resetting tools outside the scope of this displayer)
let queryhook = function() {
	$('#status').html("Querying service...");
}

// Build and execute the displayer.
let displayer = new AttedDisplayer(opts, callback, queryhook);
```

## Development

The displayer uses a grunt based build process to browserify the code.

Upon initial cloning of the repo, install the node modules:

<code>npm install</code>

Then build the project:

<code>npm run setup</code>

The build process runs automatically when files in the /src folder are modified:

<code>npm start</code>

To view the tool, serve the home directory (in a separate terminal window):

<code>serve -p 9001</code>

or

<code>python -m SimpleHTTPServer 9001</code>


