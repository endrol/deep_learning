## violinplot

we use seaborn to plot violinplot, [this link](https://seaborn.pydata.org/generated/seaborn.violinplot.html) shows how we use violinplot.

### Basic Knowledge
violinplot gives a straight forwadrd understanding about data distribution.  

#### Box plot
A box and whisker plot, also called a box plot, displays the five-number summary of a set of data. The five-number summary is the **minimum**, **first quartile**, **median**, **third quartile**, and **maximum**. These five elements show how data distributed. We can see the range of the dataset and the median (can be considered most data). 

| |
|---|
|<img src="./image_resources/boxplot.png" width=400 class="center">|

#### Kernel Density Estimation  
[This page](https://mathisonian.github.io/kde/) gives a intuitive understanding about Kernel Density Estimation. Basically we can see diferent curves based on different kernel and bandwidth. Compare to BoxPlot, KDE has a continous boundry about the distribution of the data, yet we don't know the exact five-elemrnt infos. 

Violinplot conbines info from both boxplot and KDE. We can see a rough data-gathering information (boxplot) as well as the continous distribution (KDE). This allows us has a grasp about dataset.  
<img src="./image_resources/seaborn-violinplot-2.png" width=400 class="center">  

### Usage
For most usage, the *seaborn page* shall gives us the hint. However, for more usage like changing the text information or, saving multiple plots or, display subplots, we can always use **matploblib** to as a wraping function.
```
sns.set_theme(style='whitegrid')
            csv_data = pd.read_csv('metric.csv')
            plt.figure(figsize=(10, 5))

            ax_error = sns.violinplot(x="ground_truth_label",
                y="error",
                data=csv_data,
                inner='box',
                bw=0.08,
                split=True,
                hue="error_type")

            medians = csv_data.groupby(['ground_truth_label'])['error'].median().values
            nobs = csv_data['ground_truth_label'].value_counts().values // 3
            nobs = [str(x) for x in nobs.tolist()]
            nobs = ["n: "+i for i in nobs]
            pos = range(len(nobs))
            for tick, label in zip(pos, ax_error.get_xticklabels()):
                ax_error.text(pos[tick], medians[tick] - 0.5, nobs[tick],
                        horizontalalignment='center',
                        size='small',
                        color='r',
                        weight='semibold')
            ax_error.set_title("width threshold "+str(args.width_thresh/rows*100)+"%")
            plt.savefig("error_left_right")

            plt.figure(figsize=(10,5))
            ax_error_length = sns.violinplot(x="ground_truth_label",
                y="error_length",
                data=csv_data,
                inner='box',
                bw=0.08)
            medians = csv_data.groupby(['ground_truth_label'])['error_length'].median().values
            nobs = csv_data['ground_truth_label'].value_counts().values // 3
            nobs = [str(x) for x in nobs.tolist()]
            nobs = ["n: "+i for i in nobs]
            pos = range(len(nobs))
            for tick, label in zip(pos, ax_error_length.get_xticklabels()):
                ax_error_length.text(pos[tick], medians[tick] - 0.5, nobs[tick],
                        horizontalalignment='center',
                        size='small',
                        color='r',
                        weight='semibold')
            ax_error_length.set_title("width threshold "+str(args.width_thresh/rows*100)+"%")
            plt.savefig("error_length")
```
