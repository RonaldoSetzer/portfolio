---
layout: open-source
title: "Palidor"
site-category: "Framework/Extension"
permalink: /open_source/palidor/

#components
list: ["cover-img", "content", ]

#cover img
cover-img: "thumb_palidor.png"

#urls
github-url: https://github.com/RonaldoSetzer/robotlegs-extensions-Palidor/
web-page-url: https://ronaldosetzer.github.io/robotlegs-extensions-Palidor/
---

<div class="row" style="padding: 25px 25px 25px 25px;">
    <h3 class="text-center">Palidor Bundle</h3>
    <hr class="star-primary">
    <p>Palidor is an extension to integrates Robotlegs and Starling, which contains:</p>
    <ul>
        <li><p>StarlingIntegration</p></li>
        <li><p>StarlingContextView</p></li>
        <li><p>StarlingViewMap</p></li>
        <li><p>StarlingMediator</p></li>
        <li><p>StarlingViewManager</p></li>
        <li><p>StarlingCommandMap</p></li>
        <li><p>FlowManager</p></li>
        <li><p>SignalCommandMap</p></li>
        <li><p>KeyCommandMap</p></li>
        <li><p>KeyDispatcher</p></li>
    </ul>
</div>

<div class="row" style="padding: 25px 25px 25px 25px;">
    <h3 class="text-center">Dependencies</h3>
    <hr class="star-primary">
    <ul>
        <li><p><a href="https://github.com/Gamua/Starling-Framework">Starling</a></p></li>
        <li><p><a href="https://github.com/robotlegs/robotlegs-framework">Robotlegs 2</a></p></li>
        <li><p><a href="https://flex.apache.org/download-flexunit.html">FlexUnit 4</a></p></li>
        <li><p><a href="https://github.com/robertpenner/as3-signals">as3-signals</a></p></li>
    </ul>
</div>
<div class="row text-center" style="padding: 25px 25px 25px 25px;">
    <h3>More Details</h3>
    <hr class="star-primary">

    <a href="{{ page.web-page-url }}" class="btn btn-lg btn-primary"><i class="fa fa-link"></i> Web Page</a>
    <a href="{{ page.github-url }}" class="btn btn-lg btn-primary"><i class="fa fa-github"></i> GitHub</a>
</div>
<div class="row" style="padding: 25px 25px 25px 25px;">
    <h3 class="text-center">Basic Usage</h3>
    <hr class="star-primary">


    <h4>Setup</h4>

    <div class="highlight"><pre>
    <span class="kd">const</span> robotlegsContext:<span class="kt">IContext</span> = <span class="k">new</span> <span class="nc">Context</span>();
    robotlegsContext.<span class="na">install</span>( <span class="nc">PalidorBundle</span> );
    robotlegsContext.<span class="na">configure</span>( <span class="nc">YourConfig</span>, starling, <span class="k">new</span> <span class="nc">ContextView</span>( <span class="k">this</span> ) );
    </pre></div>

    <h4>IConfig Example</h4>

    <div class="highlight"><pre>
    <span class="kd">public</span> <span class="kd">class</span> YourConfig<span class="kd"> implements </span>IConfig
    <span class="o">{</span>
        <span class="nt">[Inject]</span>
        <span class="kd">public</span> <span class="kd">var</span> eventDispatcher:<span class="kt">EventDispatcher</span>; <span class="c">//starling.events.EventDispatcher</span>

        <span class="nt">[Inject]</span>
        <span class="kd">public</span> <span class="kd">var</span> mediatorMap:<span class="kt">IMediatorMap</span>;

        <span class="nt">[Inject]</span>
        <span class="kd">public</span> <span class="kd">var</span> context:<span class="kt">IContext</span>;

        <span class="nt">[Inject]</span>
        <span class="kd">public</span> <span class="kd">var</span> flowManager:<span class="kt">IFlowManager</span>;

        <span class="nt">[Inject]</span>
        <span class="kd">public</span> <span class="kd">var</span> commandMap:<span class="kt">IStarlingCommandMap</span>;

        <span class="kd">public</span> <span class="kd">function </span><span class="nf">configure</span>():<span class="kt">void</span>
        <span class="o">{</span>
            context.<span class="na">afterInitializing</span>( initialize );
        }

        <span class="kd">private</span> <span class="kd">function </span><span class="nf">initialize</span>():<span class="kt">void</span>
        <span class="o">{</span>
            commandMap.<span class="na">map</span>( <span class="nc">CustomEvent</span>.<span class="no">COMMAND_01</span> ).<span class="na">toCommand</span>( <span class="nc">FirstCommand</span> );
            commandMap.<span class="na">map</span>( <span class="nc">CustomEvent</span>.<span class="no">COMMAND_02</span> ).<span class="na">toCommand</span>( <span class="nc">SecondCommand</span> );

            mediatorMap.<span class="na">map</span>( <span class="nc">FirstView</span> ).<span class="na">toMediator</span>( <span class="nc">FirstViewMediator</span> );
            mediatorMap.<span class="na">map</span>( <span class="nc">FirstFloatingView</span> ).<span class="na">toMediator</span>( <span class="nc">FirstFloatingViewMediator</span> );

            flowManager.<span class="na">map</span>( <span class="nc">CustomEvent</span>.<span class="no">SHOW_FIRST_VIEW</span> ).<span class="na">toView</span>( <span class="nc">FirstView</span> );
            flowManager.<span class="na">map</span>( <span class="nc">CustomEvent</span>.<span class="no">SHOW_FIRST_FLOATING_VIEW</span> ).<span class="na">toFloatingView</span>( FirstFloatingView );

            eventDispatcher.<span class="na">dispatchEventWith</span>( <span class="nc">CustomEvent</span>.<span class="no">SHOW_FIRST_VIEW</span> );
        }
    }</pre></div>

</div>
