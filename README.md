<!--You must include this JavaScript file -->
<script src="https://assets.crowd.aws/crowd-html-elements.js"></script>
<!DOCTYPE html>
<html lang="en">
 
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.6.0/dist/jquery.min.js"></script>
 
 
    <title>Document</title>
</head>
 
<body>
   <style>
        .pro {
            width: 220px;
            height: 40px;
            background-color: #C8C8C8;
            text-align: left;
            line-height: 40px;
            /*border-radius: 50px;*/
            border: 1px solid black;
            display: inline-block;
        }
 
        .pro1 {
            /* width: 100px;
            height: 40px; */
            background-color:#C8C8C8;
            /*text-align: center;*/
            line-height: 40px;
            /*border-radius: 50px;*/
            border: 1px solid black;
            display: none;
            /* 先设置隐藏 */
            width: 1000px;
            position: fixed;
            top:0;
            left:0;
            z-index:9999;
        }
    </style>
 <!--For the full list of available Crowd HTML Elements and their input/output documentation,-->
 <!--     please refer to https://docs.aws.amazon.com/sagemaker/latest/dg/sms-ui-template-reference.html -->-->

 <!--You must include crowd-form so that your task submits answers to MTurk -->
<crowd-form answer-format="flatten-objects">

  <crowd-instructions link-text="View instructions" link-type="button">
    <short-summary>
      <p>In this task, you are given a paragraph and a pair of two events which are included and annotated in the paragraph. You will be asked to decide which of the two events happens first and complete an explanation to illustrate how you make the decision.</p>
    </short-summary>

    <detailed-instructions>
      <h3>Instructions</h3>
      <p><b>Step 1: assign temporal order relation</b></p>
<p>The first step is to assign a temporal order relation for the eventA and eventB in the event pair by comparing each of the events' <b>starting</b> point. You should also rate how likely the temporal order relation is.</p>

<p>Use "<mark>before</mark>" to represent that eventA started before eventB started.</p>

<p>Use "<mark>after</mark>" to represent that eventA started after eventB started.</p> 

<p>Use "<mark>equal</mark>" to represent eventA and eventB started at the exact same time.</p> 

<p>Use "<mark>vague</mark>" if you cannot tell an order between the two.</p>

<p>After deciding the temporal order relation:</p> 

<p>Use "<span style="background-color: red">certain</span>" to represent that you think your annotated relation is 100% certain to be true.</p> 

<p>Use "<span style="background-color: red">most likely</span>" to represent that you think your annotated relation is more than 80% certain to be true.</p> 

<p>Use "<span style="background-color: red">likely</span>" to represent that you think your annotated relation is more than 50% certain to be true.</p>

<p><b>Step 2: select all relevant explanation classes</b></p>
<p>You are now asked to choose all relevant explanation classes that help you (or you use) to decide the temporal order relation of the event pair and write down simple phrases to further explain the class content <b>in a reasoning logic order</b>.</p>

<!--<p>You should first take into consideration two major explanation directions: explicit clues in content and commonsense. Explicit clues in content refer to the clues that can be extracted directly from the paragraph like timestamp and grammar. While commonsense requires to be inferred from the paragraph like prerequisites.</p>   -->

<!--<p>We then identify 6 major classes under this two directions: timestamp, grammar, explicit temporal connection for explicit clues in content; event type, prerequisites and temporal property for commonsense.</p>-->

<p>In general, you can choose from the 6 classes.</p> <!-- aforementioned -->

<p>1. <b>timestamp</b>: an explicit or easy-to-infer time annotation for an event in the paragraph. For example, "I <b>ate</b> snacks at 9pm". "at 9pm" is the explicit timestamp for event "ate snacks". While for Mr Lowe said of his Antarctic adventure: "We estimated we could do it in 100 days, and we got across on the 99th day". "We were <b>pleased</b> that England and New Zealand knew about it, and we thought that's where it would stop."  "on the 99th day" is the easy-to-infer timestamp for event "pleased".</p>

<p>2. <b>grammar</b>: the way words are used to make sentences. No matter what events are in the sentence, the event order relation remains the same for the same grammar.</p>

<p>3. <b>explicit temporal connection</b>: connection like at the same time / before / after mentioned in the content for an event. For example, "I ate snacks before sleep". "before sleep" is the explicit temporal connection for event "ate snacks".</p>

<p>4. <b>event type</b>: you can choose from: state / action / thought. State indicates that it is a long-time action and thought indicates that the event is not happening. It is in the future or imaginary.</p>

<p>5. <b>prerequisites</b>: eventA/ eventB is required as a prior condition for eventB / eventA to happen or exist. The condition can be relaxed to your intuition, but the relation should exist in most situations.</p>

<p>6. <b>temporal property</b>: You can choose from duration / frequency / typical time. <b>Duration</b> is the lasting time of the event:you can choose from "second”, “minute”, “hour”, “day”, “week”,"year","lifetime". <b>Frequency</b> is the happening frequency of the event: you may choose from “every”, “per”, “once”, . . ., “times”. <b>Typical time</b> is the typical happening time of the event: including the time of day (e.g., “morning” etc.), time of week (e.g., “Monday” etc.), month (e.g., “January” etc.) and season (e.g., “winter” etc.). </p>
    </detailed-instructions>
    
    
     <positive-example>
      <p><b>Example1</b></p>
      <p><b>Passage:</b>Speaking to the BBC in 1995, Mr Lowe said of his Antarctic adventure: "We estimated we could do it in 100 days, and we got across on the 99th day". "We were <b>pleased</b> that England and New Zealand knew about it, and we thought that's where it would stop." He also talked about his "second job" as the group's cameraman, and having to <b>wear</b> four pairs of gloves to work the clockwork camera.</p>
      <p><b>Event pair:</b> "pleased" and "wear"</p>
      <p><b>Temporal order relation:</b> after</p>
      <p><b>Certainty level:</b> certain</p>
      <p><b>Explaination:</b></p>
      <p>1:Mr Lowe was pleased after they got across on the 99th day.</p>
      <p>5:The event that he wears four pairs of gloves happens before the end of the adventure.</p>
      <br /> 
      <p><b>Example2</b></p>
      <p><b>Passage:</b> I went to sleep, woke up in the morning, went down stairs and met Ben there. He was holding a coffee, which he just purchased at a nearby shop.</p>
      <p><b>Event pair:</b> "went to sleep" and "purchased a coffee"</p>
      <p><b>Temporal order relation:</b> before</p>
      <p><b>Certainty level:</b> certain</p>
      <p><b>Explaination:</b></p>
      <p>2:I went to sleep before I met Ben.</p>
      <p>2:I met Ben at the same time when he was holding a coffee.</p>
      <p>5:Normally someone purchasing a coffee happened and ended before he was holding a coffee. So Ben purchased a coffee before I met Ben.</p>
      <p>6:Hour for duration of “ sleep”, minute for duration of “Ben purchased a coffee”.</p>
      <br /> 
      <p><b>Example3</b></p>
      <p><b>Passage:</b>People lay their hands on Deazjah Roseboro, 12, as she comforts her cousin, Jerney Moss, 8, following a mass shooting at a Tops Friendly Market in Buffalo, NY, on Sunday, May 15. </p>
      <p><b>Event pair:</b>"lay their hands" and "comforts"</p>
      <p><b>Temporal order relation:</b> equal</p>
      <p><b>Certainty level:</b> certain</p>
      <p><b>Explaination:</b></p>
      <p>3:People lay their hands on Deazjah Roseboro at the same time as she comforts her cousin.</p>
      
    </positive-example>

    <!--<negative-example>-->
    <!--  <p>Provide an example of a bad answer here</p>-->
    <!--  <p>Explain why it's a bad answer</p>-->
    <!--</negative-example> -->-->
  </crowd-instructions>
  

<p> Read the passage and decide which of the two events descirbed in the passage happens first and give an explanation of your choice:</p>

    <!-- Your contexts and intents will be substituted for the "context" and "intent" variables when you 
           publish a batch with an input file containing multiple contexts and intents -->
    <p><strong>Passage: </strong>${passage}</p>
    <p><strong>Event pair: </strong>${eventpair}</p>
    
  
 <head>
<title>multiple-choice quiz form</title>
</head>

 <!--Check the answer to each multiple-coice question that you like the best: -->

-->

<P>1. Assign a <b>temporal order relation</b> for the event pair by comparing each of the events' starting time. <BR>
<input type="radio" name="temporal order relation" value="before">before<BR>
<input type="radio" name="temporal order relation" value="after">after<BR>
<input type="radio" name="temporal order relation" value="equal">equal<BR>
<input type="radio" name="temporal order relation" value="vague">vague<BR>
</p>

<P>2. How <b>likely</b> do you think your chosen relation will happen?<BR>
<input type="radio" name="certainty" value="certain">certain (100% sure)<BR>
<input type="radio" name="certainty" value="most likely">most likely (>80% sure)<BR>
<input type="radio" name="certainty" value="likely">likely (>50% sure)<BR>
</p>

<!--<div>-->
<!--<p>Check this box if you like birds</p>-->
<!--<crowd-checkbox name="likeBirds" checked="true" required></crowd-checkbox>-->
<!--</div> --> -->

<div>
<p>3. Explain your choice of temporal order relation: <b>choose from explanation classes</b> and <b>write a sentence or two</b> to explain in detail for the class you choose.</p>
<p>You should write down an explanation including <b>only a class and a major event  in a line</b>. You can choose a class multiple times to describe multiple events.</p>
<p>The explanation sentences should be <b>logically connected</b> and all sentences together are a <b>complete and reasonable</b> explanation.</p>
<p>If you think the relation is <b>vague</b>, you should write down all the explanations you may find. If there is nothing, you can write down <b> None</b>. </p>
<p>If the event mentioned in your explanation is from the event pair, you should use the <b>exact same language</b> to describe the event.</p>
<p>For each line, <b>the format is</b>: Number for the class you choose(1-6): explanation sentence. (addiational sentence: <b>So</b> <b>Event in the pair</b> (happen) before/after/at the same time as <b>Event2</b>). You may <b>further add a sentence</b> to compare event with the events in the event pair, which will assist in explanation.</p>

<br>
<!--<div style="display: flex;">-->
    
<p>You can choose from the following classes and click on the class name to see a detailed definition:</p>
<p>The content in brackets like (the event of) is optional and can be used to complete a sentence.</p>
<p><div class="pro"><div>1.Timestamp</div>
            <div class="pro1">
                <div> An explicit or easy-to-infer time annotation for an event in the paragraph. For example, "I <b>ate</b> snacks at 9pm". "at 9pm" is the explicit timestamp for event "ate snacks". While for Mr Lowe said of his Antarctic adventure: "We estimated we could do it in 100 days, and we got across on the 99th day". "We were <b>pleased</b> that England and New Zealand knew about it, and we thought that's where it would stop."  "on the 99th day" is the easy-to-infer timestamp for event "pleased".</p>
</div>
            </div>
        </div> Line format: <b>1:</b> (The event of) <b>Event</b> (happen) at <b>Timestamp</b>. </p> 
    <!---- 1. <b>Timestamp</b>. -->
<!--<html>-->
<!--	<div id="test"></div>-->
<!--	<button type="button" onclick="changetext();">Click Me!</button>-->
<!--<script type="text/javascript">-->
<!--	function changetext(){-->
<!--	document.getElementById("test").innerHTML = "New text!";}-->
<!--</script>-->
<!--</html>-->
<p><div class="pro"><div>2.Grammar</div>
            <div class="pro1">
                <div> The way words are used to make sentences. No matter what events are in the sentence, the event order relation remains the same for the same grammar.</p>
</div>
            </div>
        </div> Line format: <b>2:</b> <b>Event1</b> (happen) before/after/at the same time as <b>Event2</b>. </p> 
<!--<p>  -- 2. <b>Grammar</b>. Format: <b>2:</b> <b>Event1</b> (happen) before/after/at the same time as <b>Event2</b>.</p>-->

<p><div class="pro"><div>3.Explicit temporal connection</div>
            <div class="pro1">
                <div> Connection like at the same time / before / after mentioned in the content for an event. For example, "I ate snacks before sleep". "before sleep" is the explicit temporal connection for event "ate snacks".</p>
</div>
            </div>
        </div> Line format: <b>3:</b> <b>Event</b> (happen) <b>explicit temporal connection</b>. </p> 
        
<!--<p>  -- 3. <b>Explicit temporal connection</b>. Format: <b>3:</b> <b>Event</b> (happen) <b>explicit temporal connection</b>.</p>-->

<p><div class="pro"><div>4.Event type</div>
            <div class="pro1">
                <div> You can choose from: state / action / thought. State indicates that it is a long-time action and thought indicates that the event is not happening. It is in the future or imaginary.</p>
</div>
            </div>
        </div> Line format: <b>4:</b> The event type of <b>Event</b> is action/state/thought. Action indicates that it lasts for a short time/State indicates that it is a long-time action/Thought indicates that the event is not happening.  </p> 
        
<!--<p>  -- 4. <b>Event type</b>. Format: <b>4:</b> The event type of <b>Event</b> is action/state/thought. Action indicates that it lasts for a short time/State indicates that it is a long-time action/Thought indicates that the event is not happening. </p>-->

<p><div class="pro"><div>5.Prerequisites</div>
            <div class="pro1">
                <div> EventA/ eventB is required as a prior condition for eventB / eventA to happen or exist. The condition can be relaxed to your intuition, but the relation should exist in most situations.</p>
</div>
            </div>
        </div> Line format: <b>5:</b> Normally <b>Event1</b> happens and ends before <b>Event2</b>. </p>  
<!--<p>  -- 5. <b>Prerequisites</b>. Format: <b>5:</b> Normally <b>Event1</b> happens and ends before <b>Event2</b>.</p>-->

<p><div class="pro"><div>6.Temporal property</div>
            <div class="pro1">
                <div> You can choose from duration / frequency / typical time. <b>Duration</b> is the lasting time of the event:you can choose from "second”, “minute”, “hour”, “day”, “week”,"year","lifetime". <b>Frequency</b> is the happening frequency of the event: you may choose from “every”, “per”, “once”, . . ., “times”. <b>Typical time</b> is the typical happening time of the event: including the time of day (e.g., “morning” etc.), time of week (e.g., “Monday” etc.), month (e.g., “January” etc.) and season (e.g., “winter” etc.). </p>
</div>
            </div>
        </div> Line format: <b>6:</b> <b>Feature</b> for duration / frequency / typical time of <b>Event</b>.  </p>
        
<!--<p>  -- 6. <b>Temporal property</b>. Format: <b>6:</b> <b>Feature</b> for duration / frequency / typical time of <b>Event</b>. </p>-->
<crowd-text-area name="essay" rows="7" placeholder="Please enter your explanation here..." required></crowd-text-area>
</div> -->
<br>
<br>
<br>
<br>


</div>
    <script>
        $(function () {
            // .click点击弹出
            $(".pro").mousemove(function () {
                // this相当于指针，会根据鼠标自动跳
                $(".pro1", this).css("display", "block")
            })
 
            $(".pro").mouseleave(function () {
                $(".pro1", this).css("display", "none")
 
            })
        })
    </script>
 
</body>
 
</html>


</crowd-form>
