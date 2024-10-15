<script>
 function update () {
    const form = document.forms['attendee-form'];
    if (form) {
      form.addEventListener('submit', function (event) {
        event.preventDefault();
        const inputs = Array.from(form.querySelectorAll('input'));
        const values = inputs.reduce((acc, input) => {
          acc[input.id + '_out'] = input.value;
          return acc;
        }, {});

        Object.entries(values).forEach(([id, value]) => {
          const elements = document.getElementsByClassName(id);
          Array.from(elements).forEach(element => {

            console.log(element.innerHTML);
            if(Number(element.innerHTML) > 99 ){
               console.log(`Got a 99+ attendee: ${element.innerHTML}`);
               element.innerHTML = value;
             }
            else{
               console.log(`Got a sub 99 attendee: ${element.innerHTML}`);
               if(element.innerHTML.includes('gmail.com'))
               {
                element.innerHTML = `0${value}`;
                }
               else{
                element.innerHTML = value;
               }
                }
          });
        });
        const attendeeIDInput = form.elements['attendeeID'];
       if (attendeeIDInput && attendeeIDInput.value !== 'Your_Attendee_ID') {
          localStorage.setItem('attendeeID', attendeeIDInput.value);
        }
      });
    }
  };
</script>
<style>
  /* Style for the button */
  button {
    background-color: black; /* Set the background color to black */
    color: white; /* Set the text color to white */
    border: none; /* Remove the border */
    padding: 10px 20px; /* Add some padding for better appearance */
    cursor: pointer; /* Show a pointer cursor on hover */
  }

   /* Style for the input element */
  input[type="text"] {
    border: 2px solid black; /* Set the border thickness to 2px */
    padding: 5px; /* Add some padding for better appearance */

</style>

Please **`submit the form below with your Attendee or pod ID`**. All configuration entries in the lab guide will be renamed to include your pod ID.
 {: .block-warning }

<script>
document.forms["attendee-form"][1].value = localStorage.getItem("attendeeID") || "Your Attendee ID" 
</script>
<form id="attendee-form">
  <label for="attendee">Attendee ID:</label>
  <input type="text" id="attendee" name="attendee" onChange="update()"><br>
<br>
  <button onclick="update()">Save</button>
</form>

<br/>


## Learning Objectives

When callers are waiting in queue and your best agents for those calls are busy, you can use the strategy of skill relaxation to let your callers be answered by the next best agents. In some CC systems, supervisors may re-skill agents to move them to where callers are. In this lab exercise you will build upon what you already built in the previous section

#### Update the flow 

Navigate to **CUSTOMER EXPERIENCE** and **Flows** and open the MainFlow_<w class = "attendee_out">attendeeID</w>

![rank](../assets/relax/1.png)

In the previous example note which leg of the SBR flow the call went to. Edit the **QueueContact** node and check the **Skill Relaxation** section.

Set your Flow into **Edit** mode, if applicable

Enable **Skill Relaxation** and set it like below

![rank](../assets/relax/2.png)

We have now set the flow to wait for 20s after which the caller requirement will be lowered from a level of 10 to a level of 5.

#### Make a test call

Let's choose the premium caller flow. 

Place Agent 1 in "Meeting" and Agent 2 in the Available state. 

Place a call that would normally go to Agent 1. Since Agent 1 isn't available the caller will wait in queue for 20s after which the skill will be relaxed to meet the requirements of Agent 2.

#### Summary

Instead of re-skilling an agent, each caller can be subject to a skill relaxation strategy that can cater to their unique needs **without altering the skills of agents**. Instead, sill relaxation acts on a call-by-call basis.

Let's see some advanced use cases of how to route calls based on current and previous contact center performance


