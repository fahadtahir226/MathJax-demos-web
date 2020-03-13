<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>MathJax example</title>
  <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
  <script id="MathJax-script" async
          src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>
</head>

<body>
  <h4>Formula:<h4>
    <p>\(a^2 - b^2\) = (a + b)(a - b) </p>
  <h4>Derivation: </h4>
    <p>

      \begin{align}
        (a^2 - b^2)                             \\[3px]
        &\cssId{Step1}{= aa - bb <=  As\ we\ know\ x^2 = x^1 * x^1}               \\[3px]
        &\cssId{Step2}{= aa - bb + ab - ab <= Adding\ and\ subtracting\ a*b\ as\ we\ know\ the\ sum\ is\ 0}          \\[3px]
        &\cssId{Step3}{= aa + ab - bb - ab <= Rearranging\ for\ taking\ common }          \\[3px]
        &\cssId{Step4}{= a(a+b)-b(b+a) <= Taking\ a\ as\ common\ from\ first\ two\ and\ b\ from\ second\ two\  }       \\[3px]
        &\cssId{Step5}{= (a-b)(a+b) <= Taking\ a+b\ common\ as\ we\ know\ a+b\ =\ b+a\  }
      \end{align}
</p>
  <!-- <p>When \(a \ne 0\), there are two solutions to \(ax^2 + bx + c = 0\) and they are</p> -->

<div>
  <button onclick=ShowStep() id='step'>Next Step</button>  
  <button onclick=ResetSteps() id="reset">Reset Step</button>
</div>

</body>
<script type="text/javascript">
  //
  //  Use a closure to hide the local variable
  //
  (function () {
    var n = 1;
    //
    //  Make the current step be visible, and increment the step.
    //  If it is the last step, disable the step button.
    //  Once a step is taken, the reset button is made available.
    //
    window.ShowStep = function () {
// To open the reset button after first step
      document.getElementById("reset").disabled = false;

// To add next step
      document.getElementById("Step" + n++).style.display = "inline";

// To Display Current and hide previous Details
      document.getElementById("detail"+ n).style.display = "inline";
      if(document.getElementById("detail" + (n - 1)))
      document.getElementById("detail"+ (n - 1)).style.display = "none";
    }


    //
    //  Enable the step button and disable the reset button.
    //  Hide the steps.
    //
    window.ResetSteps = function () {
      document.getElementById("step").disabled = false;
      document.getElementById("reset").disabled = true;
      var i = 1, step; n = 1;
      while (step = document.getElementById("Step" + i)) {
        step.style.display = "none";
        i++
      }
    }
  })();
  </script>
<script>
  MathJax = {
    tex: {inlineMath: [['$', '$'], ['\\(', '\\)']]},
    chtml: {
      displayAlign: 'left'
    },
    startup: {
      ready: function () {
        //
        //  Do the usual startup (which does a typeset)
        //
        MathJax.startup.defaultReady();
        //
        //  When that is all done, un-hide the page
        //
        MathJax.startup.promise.then(function () {
          ResetSteps();
          document.getElementById("reset").disabled = true;
        });
      }
    }
  };
  </script>

</html>
