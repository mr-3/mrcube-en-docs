Plugin Development
=======================

.. contents:: Contents
   :depth: 2

.. |MR3| replace:: MR\ :sup:`3` \
   
In this page, we introduce the class related to develop |MR3| plugin (net.sourceforge.mr3.plugin.MR3Plugin class). We also explain how to develop |MR3| plugins and show examples of |MR3| plugins.

|MR3| Plugin Class
-----------------------------
net.sourceforge.mr3.plugin.MR3Plugin class (hereinafter, referred to as "MR3Plugin class") is an abstract class which has an abstract method (abstract public void exec()). In order to develop |MR3| plugin, firstly, create a class that inherits MR3Plugin class and overrides the exec method in the class. MR3Plugin class provides several utility methods. |MR3| plugin developers can import an instance of com.hp.hpl.mesa.rdf.jena.model.Model interface (hereinafter, referred to as "Jena Model") to |MR3| data graphs and export |MR3| data graphs to Jena Model by using the utility methods. The utility methods are shown as follows. (If you'd like to get more information, please refer to `JavaDoc MR3Plugin <http://mrcube.org/javadoc/net/sourceforge/mr3/plugin/MR3Plugin.html>`_.)

protected JDesktopPane getDesktopPane()
    Get JDesktopPane. It is used to create internal window in |MR3|.
protected void replaceRDFModel(Model model)
    Replace Jena Model with existing RDF graph in |MR3|. 
protected void mergeRDFModel(Model model)
    Merge Jena Model to existing RDF graph in |MR3|.
protected void mergeRDFSModel(Model model)
    Merge Jena Model to existing RDFS graph in |MR3|.
protected void replaceProjectModel(Model model)
    Replace Jena Model to |MR3| project. The model in this method parameter is created from a |MR3| project file.
protected Model getRDFModel()
    Get Jena Model from the RDF graph in |MR3|.
protected JGraph getRDFGraph()
    Get org.jgraph.JGraph object from the graph in RDF Editor.
protected JGraph getClassGraph()
    Get org.jgraph.JGraph object from the graph in Class Editor.
protected JGraph getPorpertyGraph()
    Get org.jgraph.JGraph object from the graph in Property Editor.
protected Model getSelectedRDFModel()
    Get Jena Model from the selected nodes in the RDF graph.
protected Model getRDFSModel()
    Get Jena Model from the RDFS graph.
protected Model getSelectedRDFSModel()
    Get Jena Model from the selected nodes in the RDFS graph.
protected Model getClassModel()
    Get Jena Model from the graph in Class Editor.
protected Model getSelectedClassModel()
    Get Jena Model from the selected nodes in the Class editor.
protected Model getPropertyModel()
    Get Jena Model from the graph in Property Editor.
protected Model getSelectedPropertyModel()
    Get Jena Model from the selected nodes in the Property editor.
protected Model getProjectModel()
    Get Jena Model from the |MR3| project.

How to develop |MR3| plugins
--------------------------------

1. Create a class that inherits MR3Plugin class and overrides public void exec() method.
2. Create a manifest file including plugin class name and the plugin name as follows. After that creating a jar file including the plugin class and the manifest file. (Plugin class name and the plugin name are necessary. Creator, date, and description attributes are options.）

.. code-block:: mf

     Name: Plugin class name
     plugin-name(or menu-name):  Plugin name
     creator: creator name
     date: update date
     description: description of the plugin
     
3. Put the crated jar file in the MR3/plugins directory or the directory that is set as class path.

When the users select Plugins sub menu in the Tool menu, the Plugins dialog is shown and developed plugins are listed in the Plugins dialog. When the users select one of the plugins and click Execute button, the exec method that is overrided in the selected Plugin class is executed.

Sample Plugins
------------------
A sample manifest file and samples plugins are described as follows. The sample plugins can be download from `MR3PluginSamples <https://github.com/mr-3/MR3PluginSamples>`_ .

A sample manifest file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: mf

    Manifest-Version: 1.0
    
    Name: net.sourceforge.mr3.plugins.samples.ReplaceRDFModelSample.class
    menu-name: ReplaceRDFModelSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: Replace RDF Model Sample Program. 
    
    Name: net.sourceforge.mr3.plugins.samples.GetRDFModelSample.class
    plugin-name: GetRDFModelSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: Get RDF Model Sample Program.
    
    Name: net.sourceforge.mr3.plugins.samples.OpenProjectSample.class
    plugin-name: OpenProjectSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: Open Project File Sample Program.
    
    Name: net.sourceforge.mr3.plugins.samples.SelectNodesSample.class
    plugin-name: SelectNodesSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: This plugin select mr3:a, mr3:b and mr3:c nodes.
    
    Name: net.sourceforge.mr3.plugins.samples.GroupNodesSample.class
    plugin-name: GroupNodesSample
    creator: Takeshi Morita
    date: 2003-12-23
    description: This plugin group mr3:a, mr3:b and mr3:c nodes.
    
    Name: org.semanticweb.mmm.mr3.owlPlugin.OWLImportPlugin.class
    menu-name: OWLImportPlugin
    creator: Takeshi Morita
    date: 2004-01-24
    description: This is owl import plugin.
    
    
List of source codes of sample plugins
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* `GetRDFModelSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/GetRDFModelSample.java>`_
* `GroupNodesSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/GroupNodesSample.java>`_
* `OWLImportPlugin.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/OWLImportPlugin.java>`_
* `OpenProjectSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/OpenProjectSample.java>`_
* `ReplaceRDFModelSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/ReplaceRDFModelSample.java>`_
* `SelectNodesSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/SelectNodesSample.java>`_
