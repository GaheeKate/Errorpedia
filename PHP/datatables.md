https://datatables.net/forums/discussion/50678/how-to-show-less-text-in-each-column#Comment_134654

css:

Plain text
1
2
3
4
5
6
.truncate {
  max-width:50px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
and JavaScript:

Plain text
1
2
3
4
5
6
7
8
9
$(document).ready( function () {
  var table = $('#example').DataTable({
    columnDefs:[{targets:1,className:"truncate"}],
    createdRow: function(row){
       var td = $(row).find(".truncate");
       td.attr("title", td.html());
  }
  });
} );
