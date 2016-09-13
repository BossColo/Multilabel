# Multilabel
A Python module that will create multi-line xlabels in matplotlib with left-side titles

Bugs:

1.  If you want to use parenthesis in the label caption (something like L (Re)), then you need to use a different font to keep everything lined up. If you don't mind not having parenthesis (or brackets), then don't worry about this.

  To change your font, just add these two lines near the beginning of your code:

  from matplotlib import rc
  
  rc('font', family='Mono')
  
2.  Be wary with changing xlim. If you have a shared xaxis, make sure that you change the xlim of the axis that you're passing to the function. Also, make certain that if you have time data on the xaxis, if you change the xlim, you use pass datetime objects to set_xlim().

To use:

from multilabel import multilabel

From there the usage is like this:

multilabel(axes, current_tick_variable, new_variables, titles=[], label_format='%.2f', time_format='%H:%M')

where axes is the axes instance that you want to put the multiple labels on, current_tick_variable is the original variable you were plotting against, new variables is a list of new variables you'd like to display, titles is a list of titles for those variables, label_format is the format for numbers that become labels (the default is any amount of numbers before the decimal and two after), and time_format is the format of times (default is Hours:Minutes, check strftime.org for codes to change that).

Here are some examples of use:

multilabel(axs[-1], epoch, [epoch, L, MLT], titles=['Time', 'L (Re)', 'MLT'])

This takes the axes from the end of a list of axes originally plotted against epoch and changes the labels to epoch, L, and MLT, and puts the titles on the left.

multilabel(axs[-1], epoch, [epoch, L, MLT])

This is the same, except it doesn't create titles.

multilabel(axs[-1], epoch, [epoch, L, MLT], time_format='%Y/%m/%d %H:%M')

I'm sure you get the idea.
