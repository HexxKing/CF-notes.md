# [Matplotlib User's Guide](https://matplotlib.org/users/index.html)

# [Matplotlib Cheatsheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Python_Matplotlib_Cheat_Sheet.pdf)


# [Matplotlib Tutorial](https://github.com/rougier/matplotlib-tutorial)
- start IPython with the command line argument `--pylab`
  - it allows interactive matplotlib sessions that have Matlab/Mathematica-like functionality.
- pyplot provides a convenient interface to the matplotlib object-oriented plotting library. 
- Matplotlib comes with a set of default settings that allow customizing all kinds of properties. You can control the defaults of almost every property in matplotlib: figure size and dpi, line width, color and style, axes, axis and grid properties, text and font properties and so on. While matplotlib defaults are rather good in most cases, you may want to modify some properties for specific cases.
- You can change the thickness and color of the line by assigning `color="blue"` or `linewidth=2.5`
- to space out your graph use `.xlim` or `ylim`
- You can change the ticks on the sides of the graphs using `.xticks` and/or `.yticks`
  - When we set tick values, we can also provide a corresponding label in the second argument list.
- Spines are the lines connecting the axis tick marks and noting the boundaries of the data area. 
  - `.spines` 
- Add a legend using `.legend`
- make notes on your graph using `.annotate`


