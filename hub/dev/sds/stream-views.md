# Stream Views
StreamViews (or stream views) provide flexibility in the use of types.
While you cannot actually change the properties of types themselves,
the stream views feature enables you to create a view of a selected Stream that appears as if you had changed the type on which it is based.
You create a stream view by choosing a source and target type then a set of mappings between properties of those two types. Using a stream view to leverage existing type properties is preferable to creating a new type, because the stream that is based on the type continues to function with its previously archived stream data intact.

StreamView is used to specify the mapping between the source and target types.
Use a PUT method to assign a stream view to a stream, and display the stream data specified for the selected stream view with a GET method. For more information, see [Reading with StreamViews](xref:sdsReadingData#reading-with-sdsstreamviews).

To assign a stream view to a stream, execute an [Update Stream Type](xref:sdsStreams#update-stream-type) call. By specifying the stream view ID, you can effectively assign the target type of the stream view to a specified stream. 

SDS attempts to determine how to map properties from the source to the target. When the mapping 
is straightforward, such as when the properties are in the same position and of the same data type, 
or when the properties have the same name, SDS will map the properties automatically. When SDS is unable to determine how to map a source property, the property is removed. If SDS encounters 
a target property that it cannot map to, the property is added and configured with a default value.
For more information, see [Stream views mapping](#stream-views-mapping) below.

## Create stream views

To work with stream views, you first need to have types, streams and streams data defined. 
Here's a simplified procedure for working with the stream view. 
For code examples, see [Work with SdsStreamViews in .NET framework](#work-with-sdsstreamviews-in-net-framework)
 and [Work with SdsStreamViews outside of .NET framework](#work-with-sdsstreamviews-outside-of-net-framework) below. 

1. Create a type that will be the source type. 
2. Create a stream that is of the type defined in step 1.
3. Write data into the stream that was created in step 2.
4. Read data from the stream to verify.
5. Create another type that will be the target type.
6. Create a stream view using the source type (step 1) and the target type (step 5).  
    - The mapping between the source and the target type happens automatically if you do not specify it in [SdsStreamViewProperty](#sdsstreamviewproperty).
7. Get [SdsStreamViewMap](#get-stream-view-map) to see how properties are mapped.
8. Read data from the stream with the stream view to verify. For more information, see [Reading with SdsStreamViews](xref:sdsReadingData#reading-with-sdsstreamviews).

## "Changing" the stream type

You use stream views to change the type that defines a stream. You cannot modify the type itself as types are immutable. 
But you can map a stream from its current type to a different type by way of stream view.

To update a type of a stream, define a stream view and do the following:
```text
   PUT api/v1/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams/{streamId}/Type?streamViewId={streamViewId}
```

For more information, see [Update Stream Type](xref:sdsStreams#update-stream-type).

