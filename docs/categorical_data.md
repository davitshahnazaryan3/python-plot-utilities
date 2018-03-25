# plot_utils.category_means

**plot_utils.category_means**(x, y, show_fig=True, fig=None, ax=None, figsize=(3,3),
                  dpi=100, title=None, ylabel='y value', rot=0, **violinplot_kwargs):

Summarize the mean values of entries of y corresponding to each distinct
category in x, and show a violin plot to visualize it.

The violin plot will show the distribution of y values corresponding to each
category in x.

#### [Parameters]
    x : <array_like>
        An vector of categorical values.
    y : <array_like>
        The target variable whose values correspond to the values in x. Must
        have the same length as x.
    show_fig : <bool>
        Whether or not to show the figure.
    fig, ax : <mpl.figure.Figure>, <mpl.axes._subplots.AxesSubplot>
        Figure and axes objects.
        If provided, the histograms are plotted on the provided figure and
        axes. If not, a new figure and new axes are created.
    figsize : tuple of two scalars
        Size (width, height) of figure in inches. (fig object passed via "fig"
        will over override this parameter)
    dpi : scalar
        Screen resolution. (fig object passed via "fig" will over override
        this parameter)
    title : <str>
        The title of the violin plot, usually the name of vector x.
    ylabel : <str>
        The label for the y axis (i.e., average y values) of the violin plot.
    rot : <float>
        The rotation (in degrees) of the x axis labels.
    **violinplot_kwargs :
        Keyword arguments to be passed to plt.violinplot().
        (https://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.violinplot.html)
        Note that this subroutine overrides the default behavior of violinplot:
        showmeans is overriden to True and showextrema to False.

#### [Returns]
    fig, ax :
        Figure and axes objects
    mean_values : <dict>
        A dictionary whose keys are the categories in x, and their corresponding
        values are the mean values in y.

-----------------------------------------

# plot_utils.positive_rate

**plot_utils.positive_rate**(x, y, show_fig=True, fig=None, ax=None, figsize='auto', dpi=100,
                  barh=True, top_n=-1, xlabel='Positive rate', ylabel='Categories'):

Calculate the proportions of the different categories in vector x that fall
into class "1" (or "True") in vector y, and optionally show a figure.

#### [Parameters]
    x : <array_like>
        An vector of categorical values.
    y : <array_like>
        The target variable of two classes. Each value in y correspond to a
        value in x (at the same index). Must have the same length as x.
        The second unique value in y will be considered as the positive class
        (for example, "True" in [True, False, True], or "3" in [1,1,3,3,1]).
    show_fig : <bool>
        Whether or not to show the figure.
    fig, ax : <mpl.figure.Figure>, <mpl.axes._subplots.AxesSubplot>
        Figure and axes objects.
        If provided, the histograms are plotted on the provided figure and
        axes. If not, a new figure and new axes are created.
    figsize : tuple of two scalars, or 'auto'
        Size (width, height) of figure in inches. (fig object passed via "fig"
        will over override this parameter). If 'auto', the figure size will be
        automatically determined from the number of distinct categories in x.
    dpi : scalar
        Screen resolution. (fig object passed via "fig" will over override
        this parameter)
    barh : <bool>
        Whether or not to show the bars as horizontal (otherwise, vertical).
    top_n : <int>
        Only shows top_n categories (ranked by their positive rate) in the
        figure. Useful when there are too many categories.
        
#### [Returns]
    fig, ax :
        Figure and axes objects
    pos_rate : <pd.Series>
        The positive rate of each categories in x.

