Plugin Development
=======================

.. contents:: Contentns
   :depth: 2
   
MR\ :sup:`3` \のプラグイン作成に関するクラス(net.sourceforge.mr3.plugin.MR3Pluginクラス)及びプラグインの作成方法について説明する．また，プラグインのサンプルを示す．

MR\ :sup:`3` \Pluginクラス
--------------------------
net.sourceforge.mr3.plugin.MR3Pluginクラス(以下，MR3Pluginクラス)は，abstract public void exec()抽象メソッドをもつ抽象クラスである．MR\ :sup:`3` \のプラグインを作成するには，MR3Pluginクラスを継承して，execメソッドをオーバーライドする．MR3Pluginクラスは，ユーティリティメソッドを提供する．プラグイン作成者は，MR3Pluginクラスが提供するユーティリティメソッドを用いることで，Jenaが提供するcom.hp.hpl.mesa.rdf.jena.model.Modelインタフェース(以下，Model)からMR\ :sup:`3` \のグラフへの変換とMR\ :sup:`3` \のグラフからJenaのModelを得ることが可能となる．以下に，ユーティリティメソッドを示す．(`JavaDoc MR3Plugin <http://mr-3.github.io/javadoc/net/sourceforge/mr3/plugin/MR3Plugin.html>`_)

protected JDesktopPane getDesktopPane()
    JDesktopPaneを得る．内部ウィンドウを作成する際に用いる．
protected void replaceRDFModel(Model model)
    Jenaが提供するModelを，MR\ :sup:`3` \のRDFグラフへ変換する．変換したRDFグラフを編集中のRDFグラフと置換する．
protected void mergeRDFModel(Model model)
    Jenaが提供するModelを，MR\ :sup:`3` \のRDFグラフへ変換する．変換したRDFグラフを編集中のRDFグラフにマージする．
protected void mergeRDFSModel(Model model)
    Jenaが提供するModelを，MR\ :sup:`3` \のRDFSグラフへ変換する．変換したRDFSグラフを編集中のRDFSグラフにマージする．
protected void replaceProjectModel(Model model)
    Jenaが提供するModelを，MR\ :sup:`3` \のプロジェクトへ変換する．引数のModelは，MR\ :sup:`3` \のプロジェクトファイル．
protected Model getRDFModel()
    MR\ :sup:`3` \のRDFグラフをJenaのModelに変換する．
protected JGraph getRDFGraph()
    RDFエディタに描かれたグラフをorg.jgraph.JGraphオブジェクトとして得る．
protected JGraph getClassGraph()
    クラスエディタに描かれたグラフをorg.jgraph.JGraphオブジェクトとして得る．
protected JGraph getPorpertyGraph()
    プロパティエディタに描かれたグラフをorg.jgraph.JGraphオブジェクトとして得る．
protected Model getSelectedRDFModel()
    選択されているMR\ :sup:`3` \のRDFグラフをJenaのModelに変換する．
protected Model getRDFSModel()
    MR\ :sup:`3` \のRDFSグラフをJenaのModelに変換する．
protected Model getSelectedRDFSModel()
    選択されているMR\ :sup:`3` \のRDFSグラフをJenaのModelに変換する．
protected Model getClassModel()
    MR\ :sup:`3` \のクラスグラフをJenaのModelに変換する．
protected Model getSelectedClassModel()
    選択されているMR\ :sup:`3` \のクラスグラフをJenaのModelに変換する．
protected Model getPropertyModel()
    MR\ :sup:`3` \のプロパティグラフをJenaのModelに変換する．
protected Model getSelectedPropertyModel()
    選択されているMR\ :sup:`3` \のプロパティグラフをJenaのModelに変換する．
protected Model getProjectModel()
    プロジェクトをJenaのModelに変換する．

プラグイン作成方法
------------------

1. MR3Pluginクラスのサブクラスを作り，public void exec()メソッドをオーバーライドする．
2. マニフェストファイルに，プラグインクラス名とプラグイン名を以下のように記述し，プラグインクラスとマニフェストファイルをjarファイルでまとめる．（プラグインクラス名とプラグイン名は必須．creator, date, descriptionはオプション．）

.. code-block:: mf

     Name: プラグインクラス名
     plugin-name(or menu-name): プラグイン名
     creator: 作者名
     date: 更新日時
     description: プラグインの説明
     
3. 作成したjarファイルをMR3/pluginsディレクトリ(または，クラスパスの通ったディレクトリ)に置く．

MR\ :sup:`3` \を起動するとファイル->プラグインにメニューが追加される．メニューを実行すると，プラグインクラスで実装したexecメソッドが実行される．

サンプルプラグイン
------------------

以下に，MR\ :sup:`3` \のプラグインの実例を示す．ここで示すプラグインは， `MR3PluginSamples <https://github.com/mr-3/MR3PluginSamples>`_ からダウンロードできる．


マニフェストファイル
~~~~~~~~~~~~~~~~~~~~

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
    
    
サンプルプラグインのソースコードリスト
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* `GetRDFModelSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/GetRDFModelSample.java>`_
* `GroupNodesSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/GroupNodesSample.java>`_
* `OWLImportPlugin.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/OWLImportPlugin.java>`_
* `OpenProjectSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/OpenProjectSample.java>`_
* `ReplaceRDFModelSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/ReplaceRDFModelSample.java>`_
* `SelectNodesSample.java <https://github.com/mr-3/MR3PluginSamples/blob/master/src/main/java/net/sourceforge/mr3/plugins/samples/SelectNodesSample.java>`_
