---
title: "Assist - Default Sentences"
---

Home Assistant comes with built-in sentences [contributed by the community](https://github.com/home-assistant/intents/) for [dozens of languages](https://developers.home-assistant.io/docs/voice/intent-recognition/supported-languages).
These sentences allow you to:

* **Turn entities on and off**
    * *"turn on the living room light"*
    * *"turn off ceiling fan"*
* **Open and close covers**
    * *"Close the garage door"*
    * *"Open kitchen window"*
* **Set the brightness and color of lights**
    * *"Change kitchen lights brightness to 50%"*
    * *"Set bed light to green"*
    
In addition to individual entities, commands can target **areas**:

* *"turn on all lights in the living room"*
* *"open windows in the kitchen"*
* *"change kitchen brightness to 50%"*
* *"set bedroom lights to green"*

Entity [aliases](/voice_control/aliases) are also matched so multiple names can be used, even in different languages.

You can extend the built-in sentences or [add your own](/voice_control/custom_sentences) to trigger any action in Home Assistant.

## View existing sentences

Broadly speaking, you can use your voice to turn things on or off, inquire about a state, or change the brightness or color of a light.

If the voice assistant doesn't understand you, you may need to rephrase your sentence a bit.
To get an idea of the specific sentences that are supported for your language, you can do the following:

1. Take a look at the test sentences:
    * On github, in the [tests](https://github.com/home-assistant/intents/tree/main/sentences) folder, open the subfolder for your language.
    * Look through the test files to see the example sentences that have been tested.
    * The second part of the file name shows the {% term intent %}, the first part shows the domain. For some domains, such as covers, fans, and light, there are specific sentences.
        The other domains are covered by the generic *homeassistant_*.

        ![Example of a folder of assistant sentence test files](/images/assist/intents-test-files.png)
        
    * The screenshot below shows sentences used to test the command to turn on the lights. Note that *Living room* here is just a place holder. 
        It could be any area that you have in your home. 

        ![Example of a set of test sentences](/images/assist/assist-test-file-light-turn-on.png)

2. View the sentence definition:
    * On github, in the [tests](https://github.com/home-assistant/intents/tree/main/tests) folder, open the subfolder for your language.
    * Open the file of interest.

        ![Sentences definition for turning on the light](/images/assist/assist-sentence-definition-01.png) 

        * () mean alternative elements.
        * [] mean optional elements.
        * <> mean an expansion rule. The view these rules, search for `expansion_rules` in the [_common.yaml](https://github.com/home-assistant/intents/blob/main/sentences/en/_common.yaml)   file.
        * The syntax is explained in detail in the [template sentence syntax documentation](https://developers.home-assistant.io/docs/voice/intent-recognition/template-sentence-syntax/).


