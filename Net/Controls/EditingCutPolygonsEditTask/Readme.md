## Cut polygons without selection edit task

  <div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53">This sample illustrates how to create a custom ArcGIS Engine edit task that can be used in conjunction with the out-of-the-box editing commands. The Cut Polygons Without Selection edit task allows the user to cut features in a polygon layer using the Sketch tool without requiring a selection.</div>  


<!-- TODO: Fill this section below with metadata about this sample-->
```
Language:              C#, VB
Subject:               Controls
Organization:          Esri, http://www.esri.com
Date:                  11/17/2017
ArcObjects SDK:        10.6
Visual Studio:         2015, 2017
.NET Target Framework: 4.5
```

### Resources

* [ArcObjects .NET API Reference online](http://desktop.arcgis.com/en/arcobjects/latest/net/webframe.htm)  
* [Sample Data Download](../../releases)  
* [What's new](http://desktop.arcgis.com/en/arcobjects/latest/net/webframe.htm#05247c04-bfd9-4e36-ae09-bc6e833c3b14.htm)  
* [Download the ArcObjects SDK for .Net from MyEsri.com](https://my.esri.com/)  

### Usage
1. Build and run the sample.   
1. Start editing.  
1. Zoom in polygon features to cut.  
1. Click the Cut Polygons Without Selection task.  
1. Click the Sketch tool.  
1. Cut a polygon (or polygons) in two or more places with the Sketch tool.  
1. Finish the sketch to perform the cut.  
1. Stop editing. See the following illustration:  



![Illustration using the edit task to split a feature without selecting it.](images/pic1.png)  
Illustration using the edit task to split a feature without selecting it.  


#### Additional information  
<div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53">The edit task is created by implementing the IEngineEditTask interface. Compiling this sample registers the edit task in the ESRI Engine Edit Tasks component category which is used to populate the ControlsEditingTaskToolControl at runtime.  </div>  
<div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53"> </div>  
<div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53">The position of the task in the ControlsEditingTaskToolControl list is controlled using the IEngineEditTask.GroupName property and the display name using the IEngineEditTask.Name property.</div>  
<div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53"> </div>  
<div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53">The IEngineEditTask.Activate method is called when the end user selects the edit task in the ControlsEditingTaskToolControl. The Activate method is used to set up listeners to the following IEngineEditEvents: </div>  
<div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53">
  <br />These event listeners set the IEngineEditSketch.GeometryType to null if the target layer does not have a polygon geometry type, thereby disabling the Sketch tool.</div>  
<div xmlns="http://www.w3.org/1999/xhtml"> </div>  
<div xmlns="http://www.w3.org/1999/xhtml" xmlns:my="http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-02-10T23:25:53">The IEngineEditTask.OnFinishSketch method is used to cut the intersected features using the IFeatureEdit.Split method, passing in the geometry from the digitized sketch as an argument. Edits to features are made in a single edit operation and added to the operation stack.  </div>  




---------------------------------

#### Licensing  
| Development licensing | Deployment licensing | 
| ------------- | ------------- | 
| Engine Developer Kit | ArcGIS Desktop Basic |  
|  | ArcGIS Desktop Standard |  
|  | ArcGIS Desktop Advanced |  
|  | Engine |  


