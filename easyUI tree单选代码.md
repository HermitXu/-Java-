 $("#"+treeId).tree({
                data: targetDbTrees,
                onSelect: function (node) {
                    var cknodes = $("#"+treeId).tree("getChecked");
                    for (var i = 0; i < cknodes.length; i++) {
                        if (cknodes[i].id != node.id) {
                            $("#"+treeId).tree("uncheck", cknodes[i].target);
                        }
                    }
                    if (node.checked) {
                        $("#"+treeId).tree('uncheck', node.target);
                    } else {
                        $("#"+treeId).tree('check', node.target);

                    }

                },
                onLoadSuccess: function (node, data) {
                    $(this).find('span.tree-checkbox').unbind().click(function () {
                        $("#"+treeId).tree('select', $(this).parent());
                        return false;
                    });
                }

            });
