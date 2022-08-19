# VisualSort

An animated visualization of sorting algorithms.
Project is made by Sai Hitesh Gorantla. It gives simple and interactive understanding of the sorting algorithms.
The main reason I choose this project to become more familiar with the javascript concepts, and CSS styling. So, I didn't use any frameworks other than HTML, CSS, and JS.

<h2>Algorithms</h2>
<h3>Animated</h3>
<ul>
<li>Bubble Sort</li>
<li>Comb Sort</li>
<li>Heap Sort</li>
<li>Insertion Sort</li>
<li>Selection Sort</li>
<li>Shell Sort</li>
</ul>


<h2>How Does It Work</h2>

<h3>Animation Object</h3>
<p>The animation object contains the frames which hold the indices of the elements to be highlighted and/or swapped.</p>
<p>The frames are essentially the stored "steps" of the algorithm.</p>

```javascript
animation = {
    "frames":[
        {
            "elements":[],
            "highlights":[0, 1]
        },
        {
            "elements":[0, 1],
            "highlights":[0, 1]
        }
        .
        .
    ]
}
```

<h3>Usage</h3>
<p>The animation object is created in a sorting algorithm. <br> Particular events are stored as frames of the animation.</p>

```javascript
class Algorithms {
    static bubble(e, order) {
        let elements = e;
        let solution = new Animation();
        let swapped = false;

        for (let i = 0; i < elements.length; ++i) {
            swapped = false;
            for (let j = 0; j < elements.length - 1; ++j) {
                solution.addFrame(new Frame([], [j, j + 1])); // Record to-be-highlighted elements

                if (order == "desc" ? elements[j] < elements[j + 1] : elements[j] > elements[j + 1]) {
                    swapped = true;

                    const temp = elements[j];
                    elements[j] = elements[j + 1];
                    elements[j + 1] = temp;

                    solution.addFrame(new Frame([j, j + 1], [j, j + 1])); // Record to-be-swapped & to-be-highlighted elements
                }
            }

            if (!swapped) {
                break;
            }
        }
        return solution;
    }
}
```

<h3>Animating the Algorithm</h3>
<p>The animation is played by a function that highlights the current elements in a frame and/or swaps them.</p>

