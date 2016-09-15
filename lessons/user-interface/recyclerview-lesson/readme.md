---
Title: RecyclerViews
Type: Lab
Duration: "1:30"
Creator:
  Name: Alan Caceres
  City: NYC
---

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) RecyclerViews

### Objectives

* Create and use custom `RecyclerView ViewHolders`
* Create and use custom `RecyclerView Adapters`
* Explain difference between the `RecyclerView` layout managers and when to use them.


### Preparation
* You should be familiar with creating custom layouts
* You should be familiar with creating custom objects / classes
* You should be familiar with creating custom `ListView` adapters
* You should be familiar with implementing and setting custom `OnClickListener`

## Introduction: RecyclerView

In last week's lesson we learned about ListViews and ListView adapters. The Android framework provided us with built in Adapters that did most of the work for us. We also learned about BaseAdapter, which allowed us to create an adapter that can handle our custom XML layouts. Today we're going to learn about the components that make up a complete implementation of RecyclerView. There are a lot of components involved so let's get started.

## Follow these steps

- Set up the `RecyclerView` in `XML`
- Get a reference to the `RecyclerView` in `Java`
- Configure `RecyclerView` with a `LayoutManager`
- Create a custom `XML` layout to use with `RecyclerView`
- Create a custom `Java` object to hold information for use in `RecyclerView`
- Create a custom `ViewHolder` that uses the `XML` layout created earlier
- Create a custom `RecyclerView Adapter` and implement the custom `ViewHolder`
- Make sure there is a list of the custom `Java` objects available for you to give
the custom `RecyclerView Adapter`
- Set `RecyclerView Adapter` on `RecyclerView` you referenced

---

### Demo: Setting up the RecyclerView components(20 min)

#### In XML

``` XML
<android.support.v7.widget.RecyclerView
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```

#### In onCreate()

``` Java
public class MainActivity extends AppCompatActivity {

    RecyclerView mRecyclerView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mRecyclerView = (RecyclerView) findViewById(R.id.recyclerview_main);

        LinearLayoutManager linearLayoutManager =
                new LinearLayoutManager(this, LinearLayoutManager.VERTICAL, false);
        mRecyclerView.setLayoutManager(linearLayoutManager);

    }
}
```

### Creating custom layout

<img src="screenshots/screen1.png" height="100px"/>

### Creating custom object

``` Java
public class CustomObject {

    String mText1;
    String mText2;
    String mText3;
    String mText4;

    public CustomObject(){
        mText1 = "Text 1";
        mText2 = "Text 2";
        mText3 = "Text 3";
        mText4 = "Text 4";
    }

    public CustomObject(String text1, String text2, String text3, String text4) {
        mText1 = text1;
        mText2 = text2;
        mText3 = text3;
        mText4 = text4;
    }

    public String getText1() {
        return mText1;
    }

    public void setText1(String text1) {
        mText1 = text1;
    }

    public String getText2() {
        return mText2;
    }

    public void setText2(String text2) {
        mText2 = text2;
    }

    public String getText3() {
        return mText3;
    }

    public void setText3(String text3) {
        mText3 = text3;
    }

    public String getText4() {
        return mText4;
    }

    public void setText4(String text4) {
        mText4 = text4;
    }
}
```

### Creating Custom ViewHolder
``` Java
public class CustomViewHolder extends RecyclerView.ViewHolder {

    public TextView mTextView1;
    public TextView mTextView2;
    public TextView mTextView3;
    public TextView mTextView4;
    public Button mButton1;
    public Button mButton2;

    public CustomViewHolder(View itemView) {
        super(itemView);

        mTextView1 = (TextView) itemView.findViewById(R.id.textview_1);
        mTextView2 = (TextView) itemView.findViewById(R.id.textview_2);
        mTextView3 = (TextView) itemView.findViewById(R.id.textview_3);
        mTextView4 = (TextView) itemView.findViewById(R.id.textview_4);
        mButton1 = (Button) itemView.findViewById(R.id.button_1);
        mButton2 = (Button) itemView.findViewById(R.id.button_2);

    }
}
```

### Creating Custom Adapter
``` Java
public class CustomRecyclerViewAdapter extends RecyclerView.Adapter<CustomViewHolder> {

    List<CustomObject> mCustomObjectsList;

    public CustomRecyclerViewAdapter(final List<CustomObject> customObjectList){
        mCustomObjectsList = customObjectList;
    }


    @Override
    public CustomViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        View parentView = LayoutInflater.from(parent.getContext()).inflate(R.layout.custom_layout, parent, false);
        CustomViewHolder viewHolder = new CustomViewHolder(parentView);
        return viewHolder;
    }

    @Override
    public void onBindViewHolder(CustomViewHolder holder, final int position) {

        holder.mTextView1.setText("A Text");
        holder.mTextView2.setText("Another Text");
        holder.mTextView3.setText("Some other Text");
        holder.mTextView4.setText("Yet another Text");

        View.OnClickListener onClickListener = new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                switch (view.getId()){
                    case R.id.button_1:
                        Toast.makeText(view.getContext(), "You clicked button 1", Toast.LENGTH_SHORT).show();
                        break;
                    case R.id.button_2:
                        Toast.makeText(view.getContext(), "You clicked button 2", Toast.LENGTH_SHORT).show();
                        break;
                    default:
                        Toast.makeText(view.getContext(), "You clicked row " + position, Toast.LENGTH_SHORT).show();
                }
            }
        };

        holder.mButton1.setOnClickListener(onClickListener);
        holder.mButton2.setOnClickListener(onClickListener);

    }

    @Override
    public int getItemCount() {
        return mCustomObjectsList.size();
    }
}
```

### Setting the adapter
``` Java
List<CustomObject> customObjects = new ArrayList<>();
Collections.fill(customObjects, new CustomObject());

mRecyclerView.setAdapter(new CustomRecyclerViewAdapter(customObjects));
```

### Completing the implementation

``` Java
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mRecyclerView = (RecyclerView) findViewById(R.id.recyclerview_main);

        LinearLayoutManager linearLayoutManager =
                new LinearLayoutManager(this, LinearLayoutManager.VERTICAL, false);
        mRecyclerView.setLayoutManager(linearLayoutManager);

        List<CustomObject> customObjects = new ArrayList<>();
        Collections.fill(customObjects, new CustomObject());

        mRecyclerView.setAdapter(new CustomRecyclerViewAdapter(customObjects));

    }
```

---

## Guided Practice (20 min)

Let's create our own implementation!

## Independent Practice (30 min)

Now that we have an implementation under our belts, let's try another one, this time you're on your own.

---

## Conclusion
- What are the different LayoutManagers?
- What are two components required to complete an implementation of RecyclerViews?
