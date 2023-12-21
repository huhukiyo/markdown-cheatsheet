Fine-Tuning Large Language Models — A Case Study from GPT-2<a name="TOP"></a>
===================

- - - - 
# 1.introduction #
Large Language Models (LLMs) have demonstrated remarkable capabilities in general tasks and garnered significant attention in recent years.  Efforts to align these models with human preferences have included methods like Supervised Fine-Tuning (SFT) and Reinforcement Learning with Human Feedback (RLHF).  
In our study, we take GPT-2 as a representative model to explore and suggest several strategies to lower the costs associated with fine-tuning LLMs.

## install ##
   pip install -r requirements.txt


#  Base Task: Supervised Fine-Tuning (SFT) #
our base task was to implement Supervised Fine-Tuning (SFT) for GPT-2 using the "HH-RLHF" dataset to facilitate its dialogue ability with human.
- Dataset Preparation
- Model finetuning Process: Using GPT-2 as the foundation model, we trained and fine-tuned it on the prepared dataset. In our training process, we've adopted an accumulated gradient update strategy. This approach involves updating the model parameters only after a certain number of forward and backward passes, which speeds up the training process.
- Periodic Assessment：
To ensure our model is learning effectively, we perform periodic evaluations after every set number of iterations. The best checkpoint (lowest evaluation loss) will be stored in the out_dir directory.
At the end, You can then run the code in (sample.py --out_dir=out-shakespeare):


    Markup: question and result here

# exploration #
## DPO & CDPO Comparative Analysis ##
We conducted an experimental comparison between Direct Preference Optimization (DPO) and Conservative Direct Preference Optimization (CDPO). Our aim was to determine the effectiveness of each approach in terms of loss and classification accuracy on the "HH-RLHF" dataset.
- Experimental Setup: We also utilized GPT-2 medium SFT model with gradient accumulation for larger batch size processing, and we employed the AdamW optimizer for training.
- Assessment: Both training and evaluation losses were measured, along with binary classification accuracy, to provide a balanced view of the model's performance.
- Findings: The CDPO algorithm demonstrated a significant reduction in variance and an accelerated rate of convergence compared to DPO. Notably, CDPO achieved the desired accuracy in half the GPU time required by DPO.
- Loss vs. Accuracy: We noted that while DPO consistently improved accuracy, the evaluation loss did not always correlate with accuracy improvement, suggesting that DPO loss may offer a biased performance estimate.
  ![](pic/DPO&CDPO.png)
    Markup :  ### put a picture here?###

#### Heading 4 ####

    Markup :  #### Heading 4 ####


Common text

    Markup :  Common text

_Emphasized text_

    Markup :  _Emphasized text_ or *Emphasized text*

~~Strikethrough text~~

    Markup :  ~~Strikethrough text~~

__Strong text__

    Markup :  __Strong text__ or **Strong text**

___Strong emphasized text___

    Markup :  ___Strong emphasized text___ or ***Strong emphasized text***

[Named Link](http://www.google.fr/ "Named link title") and http://www.google.fr/ or <http://example.com/>

    Markup :  [Named Link](http://www.google.fr/ "Named link title") and http://www.google.fr/ or <http://example.com/>

[heading-1](#heading-1 "Goto heading-1")
    
    Markup: [heading-1](#heading-1 "Goto heading-1")

Table, like this one :

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

```
First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell
```

Adding a pipe `|` in a cell :

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | \|

```
First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  |  \| 
```

Left, right and center aligned table

Left aligned Header | Right aligned Header | Center aligned Header
| :--- | ---: | :---:
Content Cell  | Content Cell | Content Cell
Content Cell  | Content Cell | Content Cell

```
Left aligned Header | Right aligned Header | Center aligned Header
| :--- | ---: | :---:
Content Cell  | Content Cell | Content Cell
Content Cell  | Content Cell | Content Cell
```

`code()`

    Markup :  `code()`

```javascript
    var specificLanguage_code = 
    {
        "data": {
            "lookedUpPlatform": 1,
            "query": "Kasabian+Test+Transmission",
            "lookedUpItem": {
                "name": "Test Transmission",
                "artist": "Kasabian",
                "album": "Kasabian",
                "picture": null,
                "link": "http://open.spotify.com/track/5jhJur5n4fasblLSCOcrTp"
            }
        }
    }
```

    Markup : ```javascript
             ```

* Bullet list
    * Nested bullet
        * Sub-nested bullet etc
* Bullet list item 2

~~~
 Markup : * Bullet list
              * Nested bullet
                  * Sub-nested bullet etc
          * Bullet list item 2

-OR-

 Markup : - Bullet list
              - Nested bullet
                  - Sub-nested bullet etc
          - Bullet list item 2 
~~~

1. A numbered list
    1. A nested numbered list
    2. Which is numbered
2. Which is numbered

~~~
 Markup : 1. A numbered list
              1. A nested numbered list
              2. Which is numbered
          2. Which is numbered
~~~

- [ ] An uncompleted task
- [x] A completed task

~~~
 Markup : - [ ] An uncompleted task
          - [x] A completed task
~~~

- [ ] An uncompleted task
    - [ ] A subtask

~~~
 Markup : - [ ] An uncompleted task
              - [ ] A subtask
~~~

> Blockquote
>> Nested blockquote

    Markup :  > Blockquote
              >> Nested Blockquote

_Horizontal line :_
- - - -

    Markup :  - - - -

_Image with alt :_

![picture alt](http://via.placeholder.com/200x150 "Title is optional")

    Markup : ![picture alt](http://via.placeholder.com/200x150 "Title is optional")

Foldable text:

<details>
  <summary>Title 1</summary>
  <p>Content 1 Content 1 Content 1 Content 1 Content 1</p>
</details>
<details>
  <summary>Title 2</summary>
  <p>Content 2 Content 2 Content 2 Content 2 Content 2</p>
</details>

    Markup : <details>
               <summary>Title 1</summary>
               <p>Content 1 Content 1 Content 1 Content 1 Content 1</p>
             </details>

```html
<h3>HTML</h3>
<p> Some HTML code here </p>
```

Link to a specific part of the page:

[Go To TOP](#TOP)
   
    Markup : [text goes here](#section_name)
              section_title<a name="section_name"></a>    

Hotkey:

<kbd>⌘F</kbd>

<kbd>⇧⌘F</kbd>

    Markup : <kbd>⌘F</kbd>

Hotkey list:

| Key | Symbol |
| --- | --- |
| Option | ⌥ |
| Control | ⌃ |
| Command | ⌘ |
| Shift | ⇧ |
| Caps Lock | ⇪ |
| Tab | ⇥ |
| Esc | ⎋ |
| Power | ⌽ |
| Return | ↩ |
| Delete | ⌫ |
| Up | ↑ |
| Down | ↓ |
| Left | ← |
| Right | → |

Emoji:

:exclamation: Use emoji icons to enhance text. :+1:  Look up emoji codes at [emoji-cheat-sheet.com](http://emoji-cheat-sheet.com/)

    Markup : Code appears between colons :EMOJICODE:
