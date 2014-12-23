//---------------------------------------------------------------------------------
//
//  ItemRenderers
//
//---------------------------------------------------------------------------------

Item renderers are major blockers for applciation performance. Understating them and writing properly helps in boosting performance.

Try to follow the below guidlines while using item renderers.

//---------------------------------------------------------------------------------
// Label Functions
//---------------------------------------------------------------------------------

Use label function if data formating is required for the data grid coloumn. For example, if the date or currency should be formatted, then use label functions.

private function date1LabelFunction(user:UserVO, coloumn:GridColumn):String
{
	return (user.date1) ? formatter.format(user.date1) : '';
}


//---------------------------------------------------------------------------------
// DefaultGridItemRenderer
//---------------------------------------------------------------------------------
By default spark datagrid uses DefaultGridItemRenderer. Hence using this will not affect the performace. This will be helpful to format the text with properties like fontColor, font, alignment etc.


//---------------------------------------------------------------------------------
// GridItemRenderer
//---------------------------------------------------------------------------------
GridItemRenderer will used for displaying display object than label. For example to display Image or DropdownList where DefaultGridItem can not be used.

override prepare method as below for updating the data. This is helpful as it is called just before updateDisplayList is called and this will be called only for the visible item in the datagrid and called everytime grid is updated.

override public function prepare(hasBeenRecycled:Boolean):void {
				if(data) lblData.text = data[column.dataField];
			}

Please follow :
1) Avoid data binding with curly braces{ }.
2) Avoid complex code and logic. Keep out side the item renderers as it will be called for each datagrid cell.
3) Use BitmapImage insted of Image for displaying images and Embed them for better performace.
4) Keep common function outside the renderer. May be in parent document.
5) Avoid multiple containers.
6) Give fixed with and position values so that it will not calculate the values dynamically and performance will be  better.



