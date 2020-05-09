<div>
    <h2 class="">Pandas Cheat Sheet: Guide</h2>
    <p><code>df</code>&nbsp;| Any pandas DataFrame object<br><code>s</code>&nbsp;| Any pandas Series object </p>
    <p>As you scroll down, you'll see we've organized related commands using subheadings so that you can quickly
        search for and find the correct syntax based on the task you're trying to complete.</p>
    <p>Also, a quick reminder — to make use of the commands listed below, you'll need to first import the relevant
        libraries like so:</p>
    <pre><code>import pandas as pd<br>import numpy as np</code></pre>
    <h2>Importing Data</h2>
    <p>Use these commands to import data from a variety of different sources and formats.</p>
    <p><code>pd.read_csv(filename)</code>&nbsp;| From a CSV file<br><code>pd.read_table(filename)</code>&nbsp;| From
        a delimited text file (like TSV)<br><code>pd.read_excel(filename)</code>&nbsp;| From an Excel
        file<br><code>pd.read_sql(query, connection_object)</code>&nbsp;| Read from a SQL
        table/database<br><code>pd.read_json(json_string)</code>&nbsp;| Read from a JSON formatted string, URL or
        file.<br><code>pd.read_html(url)</code>&nbsp;| Parses an html URL, string or file and extracts tables to a
        list of dataframes<br><code>pd.read_clipboard()</code>&nbsp;| Takes the contents of your clipboard and
        passes it to&nbsp;<code>read_table()</code><br><code>pd.DataFrame(dict)</code>&nbsp;| From a dict, keys for
        columns names, values for data as lists</p>
    <h2>Exporting Data</h2>
    <p>Use these commands to export a DataFrame to CSV, .xlsx, SQL, or JSON.</p>
    <p><code>df.to_csv(filename)</code>&nbsp;| Write to a CSV file<br><code>df.to_excel(filename)</code>&nbsp;|
        Write to an Excel file<br><code>df.to_sql(table_name, connection_object)</code>&nbsp;| Write to a SQL
        table<br><code>df.to_json(filename)</code>&nbsp;| Write to a file in JSON format</p>
    <h2>Create Test Objects</h2>
    <p>These commands can be useful for creating test segments.</p>
    <p><code>pd.DataFrame(np.random.rand(20,5))</code>&nbsp;| 5 columns and 20 rows of random
        floats<br><code>pd.Series(my_list)</code>&nbsp;| Create a series from an
        iterable&nbsp;<code>my_list</code><br><code>df.index = pd.date_range('1900/1/30', periods=df.shape[0])</code>&nbsp;|
        Add a date index</p>
    <h2>Viewing/Inspecting Data</h2>
    <p>Use these commands to take a look at specific sections of your pandas DataFrame or Series.</p>
    <p><code>df.head(n)</code>&nbsp;| First n rows of the DataFrame<br><code>df.tail(n)</code>&nbsp;| Last n rows of
        the DataFrame<br><code>df.shape</code>&nbsp;| Number of rows and columns<br><code>df.info()</code>&nbsp;|
        Index, Datatype and Memory information<br><code>df.describe()</code>&nbsp;| Summary statistics for numerical
        columns<br><code>s.value_counts(dropna=False)</code>&nbsp;| View unique values and
        counts<br><code>df.apply(pd.Series.value_counts)</code>&nbsp;| Unique values and counts for all columns</p>
    <h2>Selection</h2>
    <p>Use these commands to select a specific subset of your data.</p>
    <p><code>df[col]</code>&nbsp;| Returns column with label col as Series<br><code>df[[col1, col2]]</code>&nbsp;|
        Returns columns as a new DataFrame<br><code>s.iloc[0]</code>&nbsp;| Selection by
        position<br><code>s.loc['index_one']</code>&nbsp;| Selection by index<br><code>df.iloc[0,:]</code>&nbsp;|
        First row<br><code>df.iloc[0,0]</code>&nbsp;| First element of first column</p>
    <h2>Data Cleaning</h2>
    <p>Use these commands to perform a variety of data cleaning tasks.</p>
    <p><code>df.columns = ['a','b','c']</code>&nbsp;| Rename columns<br><code>pd.isnull()</code>&nbsp;| Checks for
        null Values, Returns Boolean Arrray<br><code>pd.notnull()</code>&nbsp;| Opposite
        of&nbsp;<code>pd.isnull()</code><br><code>df.dropna()</code>&nbsp;| Drop all rows that contain null
        values<br><code>df.dropna(axis=1)</code>&nbsp;| Drop all columns that contain null
        values<br><code>df.dropna(axis=1,thresh=n)</code>&nbsp;| Drop all rows have have less than n non null
        values<br><code>df.fillna(x)</code>&nbsp;| Replace all null values with
        x<br><code>s.fillna(s.mean())</code>&nbsp;| Replace all null values with the mean (mean can be replaced with
        almost any function from the&nbsp;<a href="https://docs.python.org/3/library/statistics.html" style="outline: none;">statistics module</a>)<br><code>s.astype(float)</code>&nbsp;|
        Convert the datatype of the series to float<br><code>s.replace(1,'one')</code>&nbsp;| Replace all values
        equal
        to&nbsp;<code>1</code>&nbsp;with&nbsp;<code>'one'</code><br><code>s.replace([1,3],['one','three'])</code>&nbsp;|
        Replace all 1
        with&nbsp;<code>'one'</code>&nbsp;and&nbsp;<code>3</code>&nbsp;with&nbsp;<code>'three'</code><br><code>df.rename(columns=lambda x: x + 1)</code>&nbsp;|
        Mass renaming of columns<br><code>df.rename(columns={'old_name': 'new_ name'})</code>&nbsp;| Selective
        renaming<br><code>df.set_index('column_one')</code>&nbsp;| Change the
        index<br><code>df.rename(index=lambda x: x + 1)</code>&nbsp;| Mass renaming of index</p>
    <h2>Filter, Sort, and Groupby</h2>
    <p>Use these commands to filter, sort, and group your data.</p>
    <p><code>df[df[col] &gt; 0.5]</code>&nbsp;| Rows where the column&nbsp;<code>col</code>&nbsp;is greater
        than&nbsp;<code>0.5</code><br><code>df[(df[col] &gt; 0.5) &amp; (df[col] &lt; 0.7)]</code>&nbsp;| Rows
        where&nbsp;<code>0.7 &gt; col &gt; 0.5</code><br><code>df.sort_values(col1)</code>&nbsp;| Sort values by
        col1 in ascending order<br><code>df.sort_values(col2,ascending=False)</code>&nbsp;| Sort values
        by&nbsp;<code>col2</code>&nbsp;in descending
        order<br><code>df.sort_values([col1,col2],ascending=[True,False])</code>&nbsp;| Sort values
        by&nbsp;<code>col1</code>&nbsp;in ascending order then&nbsp;<code>col2</code>&nbsp;in descending
        order<br><code>df.groupby(col)</code>&nbsp;| Returns a groupby object for values from one
        column<br><code>df.groupby([col1,col2])</code>&nbsp;| Returns groupby object for values from multiple
        columns<br><code>df.groupby(col1)[col2]</code>&nbsp;| Returns the mean of the values
        in&nbsp;<code>col2</code>, grouped by the values in&nbsp;<code>col1</code>&nbsp;(mean can be replaced with
        almost any function from the&nbsp;<a href="https://docs.python.org/3/library/statistics.html" style="outline: none;">statistics
            module</a>)<br><code>df.pivot_table(index=col1,values=[col2,col3],aggfunc=mean)</code>&nbsp;| Create a
        pivot table that groups by&nbsp;<code>col1</code>&nbsp;and calculates the mean
        of&nbsp;<code>col2</code>&nbsp;and&nbsp;<code>col3</code><br><code>df.groupby(col1).agg(np.mean)</code>&nbsp;|
        Find the average across all columns for every
        unique&nbsp;<code>col1</code>&nbsp;group<br><code>df.apply(np.mean)</code>&nbsp;| Apply the
        function&nbsp;<code>np.mean()</code>&nbsp;across each column<br><code>nf.apply(np.max,axis=1)</code>&nbsp;|
        Apply the function&nbsp;<code>np.max()</code>&nbsp;across each row</p>
    <h2>Join/Combine</h2>
    <p>Use these commands to combine multiple dataframes into a single one.</p>
    <p><code>df1.append(df2)</code>&nbsp;| Add the rows in&nbsp;<code>df1</code>&nbsp;to the end
        of&nbsp;<code>df2</code>&nbsp;(columns should be
        identical)<br><code>pd.concat([df1, df2],axis=1)</code>&nbsp;| Add the columns
        in&nbsp;<code>df1</code>&nbsp;to the end of&nbsp;<code>df2</code>&nbsp;(rows should be
        identical)<br><code>df1.join(df2,on=col1,how='inner')</code>&nbsp;| SQL-style join the columns
        in&nbsp;<code>df1</code>&nbsp;with the columns on&nbsp;<code>df2</code>&nbsp;where the rows for
        <code>col</code>&nbsp;have identical values.&nbsp;<code>'how'</code> can be one
        of&nbsp;<code>'left'</code>,&nbsp;<code>'right'</code>,&nbsp;<code>'outer'</code>,&nbsp;<code>'inner'</code>
    </p>
    <h2>Statistics</h2>
    <p>Use these commands to perform various statistical tests. (These can all be applied to a series as well.)</p>
    <p><br><code>df.describe()</code>&nbsp;| Summary statistics for numerical
        columns<br><code>df.mean()</code>&nbsp;| Returns the mean of all columns<br><code>df.corr()</code>&nbsp;|
        Returns the correlation between columns in a DataFrame<br><code>df.count()</code>&nbsp;| Returns the number
        of non-null values in each DataFrame column<br><code>df.max()</code>&nbsp;| Returns the highest value in
        each column<br><code>df.min()</code>&nbsp;| Returns the lowest value in each
        column<br><code>df.median()</code>&nbsp;| Returns the median of each column<br><code>df.std()</code>&nbsp;|
        Returns the standard deviation of each column</p>
</div>
<br>
<p>Source  -  <a href="https://www.dataquest.io/blog/pandas-cheat-sheet">dataquest</a></p>