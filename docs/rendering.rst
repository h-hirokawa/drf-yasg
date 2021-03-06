##################
Serving the schema
##################

************************************************
``get_schema_view`` and the ``SchemaView`` class
************************************************

The :func:`.get_schema_view` function and the :class:`.SchemaView` class it returns (click links for documentation)
are intended to cover the majority of use cases one might want to configure. The class returned by
:func:`.get_schema_view` can be used to obtain view instances via :meth:`.SchemaView.with_ui`,
:meth:`.SchemaView.without_ui` and :meth:`.SchemaView.as_cached_view` - see :ref:`readme-quickstart`
in the README for a usage example.

You can also subclass :class:`.SchemaView` by extending the return value of :func:`.get_schema_view`, e.g.:

.. code:: python

    SchemaView = get_schema_view(info, ...)

    class CustomSchemaView(SchemaView):
        generator_class = CustomSchemaGenerator
        renderer_classes = (CustomRenderer1, CustomRenderer2,)

********************
Renderers and codecs
********************

If you need to modify how your Swagger spec is presented in views, you might want to override one of the renderers in
:mod:`.renderers` or one of the codecs in :mod:`.codecs`. The codec is the last stage where the Swagger object
arrives before being transformed into bytes, while the renderer is the stage responsible for tying toghether the
codec and the view.

You can use your custom renderer classes as kwargs to :meth:`.SchemaView.as_cached_view` or by subclassing
:class:`.SchemaView`.
