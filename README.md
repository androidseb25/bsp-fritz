/*Die texte mit den Bildern*/

//MainActivity.java

String[] title = new String[]{"Test1", "Test2", ....};

int[] icon = new int[]{R.drawable.ic_home_selector,
                R.drawable.ic_explore_selector, R.drawable.ic_cloud_selector,
                R.drawable.ic_today_selector, R.drawable.ic_assignment_selector,
                R.drawable.ic_settings_selector, R.drawable.ic_info_outline_selector, R.drawable.ic_public_selector};

MenuListAdapter mMenuAdapter = new MenuListAdapter(MainActivity.this, title, icon);  

// Set the MenuListAdapter to the ListView
ListView lv = (ListView) findviewbyid(///Deine Listview Resource R.id.lv);
lv.setAdapter(mMenuAdapter);
lv.setOnItemClickListener(new AdapterView.OnItemClickListener() {
                @Override
                public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                    selectItem(position);
                }
            });
            
private void selectItem(int position) {

        // Locate Position = Die angeklickte Position 0 erstes Item, 1 zweites usw.
        switch (position) {
            case 0:
                //Action durchführen mit Intent zum starten einer neuen Activity
                break;
            case 1:
                //Action durchführen mit Intent zum starten einer neuen Activity
                break;
            case ...
        }
    }

// MenuListAdapter.java

public class MenuListAdapter extends BaseAdapter {

    Context context;
    String[] mTitle;
    int[] mIcon;
    LayoutInflater inflater;

    public MenuListAdapter(Context context, String[] title, int[] icon) {
        this.context = context;
        this.mTitle = title;
        this.mIcon = icon;
    }

    @Override
    public int getCount() {
        return mTitle.length;
    }

    @Override
    public Object getItem(int position) {
        return mTitle[position];
    }

    @Override
    public long getItemId(int position) {
        return position;
    }

    public View getView(int position, View convertView, ViewGroup parent) {
        TextView txtTitle;
        ImageView imgIcon;

        inflater = (LayoutInflater) context
                .getSystemService(Context.LAYOUT_INFLATER_SERVICE);
        View itemView = inflater.inflate(R.layout.item_row, parent,
                false);

        // Locate the TextViews in item_row.xml
        txtTitle = (TextView) itemView.findViewById(R.id.rowText);

        // Locate the ImageView in item_row.xml
        imgIcon = (ImageView) itemView.findViewById(R.id.rowIcon);

        // Set the results into TextViews
        txtTitle.setText(mTitle[position]);

        // Set the results into ImageView
        imgIcon.setImageResource(mIcon[position]);

        return itemView;
    }

}

//item_row.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="48dp"
    android:background="?android:attr/activatedBackgroundIndicator"
    android:orientation="horizontal">


    <ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_vertical"
        android:id="@+id/rowIcon"
        android:paddingLeft="16dp"
        android:src="@drawable/ic_home_selector"/>

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_vertical"
        android:layout_marginLeft="25dp"
        android:textSize="16sp"
        android:textColor="@color/selector_text_color"
        android:text="News"
        android:id="@+id/rowText" />

</LinearLayout>

//Bei Fragen einfach loslegen ^^

