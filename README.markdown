progress 1.0.0
==============

The progress module provides very lightweight progress bar support, needing only scripts and a layout with three objects.

Requirements
------------

- this file's custom function library

Integration Instructions
------------------------

1. Import all of the custom functions from this file.
2. Create a template layout to be used or duplicated later that will act as a progress bar window.
3. Copy the three items on this file's "ProgressBar" layout to that new layout.
4. Import the "progress" folder of scripts from this file into your file.

Run `progress: Test` to confirm that it's working correctly.

See the comments within the `Script Parameter Passing Readme` for instructions for passing parameters to public
scripts.

Usage
-----

If your process doesn't need a particular context, you can use the template progress bar layout created during installation. If
your process does need to have a particular context, duplicate that template layout and give it the needed context.

Before you script begins the processs, call `progress: Initiate Progress Bar ( Layout ; Steps {; Msg } )` sending the name of
the layout to use, the number of steps in the process and an optional initial message. Use `script.Param` to format the named
parameters:

    script.Param ( "Layout" ; "ProgressBar" ) &
    script.Param ( "Steps"  ; 1234 ) &
    script.Param ( "Msg"    ; "Beginning Process..." )

Within your process loop, call `progress: Initiate Progress Bar ( Step {; Msg } )` to update the progress bar, passing the current
step and an optional message. The `Msg` parameter can include the tokens "{step}" and "{steps}". These will be replaced by the
current step and the total number of steps. Both numbers will be formatted with the thousands separator. If no `Msg` parameter is
included, a default of "Step {step} of {steps}" will be used.

    script.Param ( "Step" ; 32 ) &
    script.Param ( "Msg"  ; "Processing record {step} of {steps}." )

Note that you needn't worry about whether the incrementation of the step will actually update the progress bar. The bar will only
be refreshed if it needs to be and the message will only be refreshed if it's different from the current message.

Finally, when you're finished with your process, call `progress: Close Progress Bar`.

Version History
---------------

1.0.0 - [Charles Ross][chuck] - 17-12-28

License
-------

MIT License

Copyright (c) 2017 Charles Ross

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[chuck]: mailto:chivalry@mac.com
