# jQuery-Tabledit [![GitHub version](https://badge.fury.io/gh/markcell%2FjQuery-Tabledit.svg)](http://badge.fury.io/gh/markcell%2FjQuery-Tabledit)
Inline editor for HTML tables compatible with Bootstrap.

## Options
The following options are supported:
* __url:__ link to server script (default = window.location.href)
* __inputClass:__ class for form inputs (default = 'form-control input-sm')
* __dangerClass:__ class for row when ajax request fails (default = 'danger')
* __warningClass:__ class for row when save changes (default = 'warning')
* __mutedClass:__ class for row when is removed (default = 'text-muted')
* __eventType:__ trigger to change for edit mode (default = 'click')
* __confirmText:__ text to append on remove button to confirm action (default = ' &nbsp; Confirm')
* __hideIdentifier:__ hide the column that has the identifier (default = false)
* __textSelection:__ enable text selection on editable columns (default = true)
* __editButton:__ activate edit button instead of spreadsheet style (default = true)
* __removeButton:__ activate remove button (default = true)

## Hooks
The following hooks are available:
* __onDraw():__ executed after draw the structure
* __onSuccess(data, textStatus, jqXHR):__ executed when the ajax request is completed
* __onFail(jqXHR, textStatus, errorThrown):__ executed when occurred an error on ajax request
* __onAlways():__ executed whenever there is an ajax request

## Examples
See demo page with the examples below on this link:
http://markcell.github.io/jQuery-Tabledit

```js
// Example #1
$('#example1').Tabledit({
  url: 'example.php',
  editButton: false,
  removeButton: false,
  columns: {
    // Column used to identify table row. 
    // [column_index, input_name]
    identifier: [0, 'id'],
    // Columns to transform in editable cells.
    // [[column_index, input_name], [column_index, input_name]]
    editable: [[2, 'firstname'], [3, 'lastname']]
  }
});
```

```js
// Example #2
$('#example2').Tabledit({
  url: 'example.php',
  eventType: 'dblclick',
  editButton: false,
  removeButton: false,
  hideIdentifier: true,
  textSelection: false,
  columns: {
    // Column used to identify table row.
    // [column_index, input_name]
    identifier: [0, 'id'],
    // Columns to transform in editable cells.
    // [[column_index, input_name], [column_index, input_name, select_options]]
    editable: [[1, 'car'], [2, 'color', '{"1": "Red", "2": "Green", "3": "Blue"}']]
  }
});
```

```js
// Example #3
$('#example3').Tabledit({
  url: 'example.php',
  columns: {
    identifier: [0, 'id'],
    editable: [[1, 'nickname'], [2, 'firstname'], [3, 'lastname']]
  }
});
```

```js
// Example #4
$('#example4').Tabledit({
  url: 'example.php',
  editButton: false,
  hideIdentifier: true,
  columns: {
    identifier: [0, 'id'],
    editable: [[1, 'car'], [2, 'color', '{"1": "Red", "2": "Green", "3": "Blue"}']]
  }
});
```

```js
// Example #5
$('#example5').Tabledit({
  url: 'example.php',
  removeButton: false,
  buttons: {
    edit: {
      class: 'btn btn-sm btn-primary',
      html: 'Edit'
    },
    remove: {
      class: 'btn btn-sm btn-danger',
      html: '<span class="glyphicon glyphicon-trash"></span>'
    },
    save: {
      class: 'btn btn-sm btn-success',
      html: 'Save'
    },
    cancel: {
      class: 'btn btn-sm btn-danger',
      html: 'Cancel'
    }
  },
  columns: {
    identifier: [0, 'id'],
    editable: [[1, 'nickname'], [2, 'firstname'], [3, 'lastname']]
  }
});
```

## Changelog
v1.1.0 (2015/02/08):
* Added toolbox column with edit and remove buttons.
* Added effect on table row when ajax request fails.
* Added effect on table row when changes are saved with success.
* Added 'onAlways()' hook, that is executed whenever there is an ajax request.
* Change 'onComplete(response)' hook to 'onSuccess(data, textStatus, jqXHR)'.
* Change 'onError()' hook to 'onFail(jqXHR, textStatus, errorThrown)'.
* Fixed some minor bugs.
* Minor code improvement.

v1.0.0 (2015/01/30):
* Initial release.

## License
Code released under the MIT license.