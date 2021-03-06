# AutoGridLayout
A custom implementation of GridLayout to allow having a dynamic span count, so that we can fit as many columns as we can depending on column width and screen size

### Usage

Add a custom attribute for the AutoGridLayout, in res/values/attrs.xml (create the file if it does not exist already):

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!-- ... -->

    <declare-styleable name="AutoGridLayout">
        <attr name="columnWidth" format="dimension" />
    </declare-styleable>
</resources>
~~~

In your XML layout file (replace `com.km.myproject.customview` with your own package name):

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    
    <com.km.myproject.customview.AutoGridLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:columnCount="5"
        app:columnWidth="50dp"/>
        
</FrameLayout>
~~~

Using `columnWidth` will try to calculate how many columns can fit and set the optimal span count automatically.
If not used (or failed to measure for some reason), the `columnCount` attribute will be used.
