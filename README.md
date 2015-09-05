<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv='Content-type' content='text/html; charset=utf-8'>
    <title>Basic Example</title>
    <link rel="stylesheet" href="../shared/css/base.css" />
  </head>
  <body>
    <h1>Basic Example</h1>
    <div id="container">
      <p>
        To install React, follow the instructions on
        <a href="https://github.com/facebook/react/">GitHub</a>.
      </p>
      <p>
        If you can see this, React is not working right.
        If you checked out the source from GitHub make sure to run <code>grunt</code>.
      </p>
    </div>
    <h4>Example Details</h4>
    <p>This is written in vanilla JavaScript (without JSX) and transformed in the browser.<p>
    <p>
      Learn more about React at
      <a href="https://facebook.github.io/react" target="_blank">facebook.github.io/react</a>.
    </p>
    <script src="../shared/thirdparty/es5-shim.min.js"></script>
    <script src="../shared/thirdparty/es5-sham.min.js"></script>
    <script src="../shared/thirdparty/console-polyfill.js"></script>
    <script src="../../build/react.js"></script>
    <script>
      var ExampleApplication = React.createClass({
        render: function() {
          var elapsed = Math.round(this.props.elapsed  / 100);
          var seconds = elapsed / 10 + (elapsed % 10 ? '' : '.0' );
          var message =
            'React has been successfully running for ' + seconds + ' seconds.';

          return React.DOM.p(null, message);
        }
      });

      // Call React.createFactory instead of directly call ExampleApplication({...}) in React.render
      var ExampleApplicationFactory = React.createFactory(ExampleApplication);

      var start = new Date().getTime();
      setInterval(function() {
        React.render(
          ExampleApplicationFactory({elapsed: new Date().getTime() - start}),
          document.getElementById('container')
        );
      }, 50);
    </script>
  </body>
</html>
