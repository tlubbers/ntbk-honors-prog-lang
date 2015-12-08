## What would printdown look like in action?

So far, I have only defined very rudimentary syntactical and semantical properties for printdown. Even so, I can already imagine how printdown might handle any number of use cases. 

For instance, imagine you have a brochure you designed at home using some graphic design software.  You saved the file as `brochure.pdf`, and you are ready to print it.

Now instead of adjusting the settings in the print driver, you instead include a file in the same folder named,`brochure.printdown`. 

The `brochure.printdown` file is just a text file that looks something like the following. 

```
default numcopy 1
color yes
two-sided yes left2right
papertype glossy
paperweight 100# text
```

Now when you double click the `brochure.printdown` file from the file explorer, the printdown backend handles all of the print settings for you and your document prints. 

This scenario is possible using only the syntax and semantics currently discussed. Of course the backend operations concerning print drivers will be immensely complicated, but from a users standpoint, that's how it would work. 

There are any number of problems this would address. One being, if you wanted to get the brochure printed at a print shop, you can be assured the right print settings will be used by including a printdown file. 

Speaking of printshops, this technology would lessen their work load extensively. If I would of had printdown when I was a print specialist, it would of been heaven on earth. Especially if the syntax and semantics were updated to include more advanced features. Consider the following "advanced" printdown file. 

```
color 
    yes if(page_has_img)
two-sided 
    range[yes pages(1..5), no pages(5..10)]
papertype 
    glossy if(frontside) & matte if(backside)
paperweight 
    100# text
```


