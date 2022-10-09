# QuickGridIssues
AspNetCore QuickGrid Issues

I wanted to capture a click event when the user clicks on the ID row/column.

I could not find anywhere in the QuickGrid docs (https://aspnet.github.io/quickgridsamples/datasources/) on how to accomplish this
so I tried to do this using a TemplateColumn with a button. 

	<TemplateColumn Title="ID">
		<button type="button" class="btn btn-link" @onclick="@(() => ColumnClick(context))">@context.ID</button>
	</TemplateColumn>
    
    private void ColumnClick(GROUP_MASTER item)
    {
        Console.WriteLine(item.NAME);
    }

I would expect that when I click on the button the only thing that would happen is that the NAME should be written to the console. 
If I was using an EF InMemoryDatabase then eveything works as expected. 
If I was using an SQL Server database (in this case, localdb) then I had these issues:

When clicking on the button for the first time that data is refreshed from the database. Then every click after that works as expected.
Filtered. When a filter is applied to the IQueryable then the data is refershed from the database every time a button is clicked.
