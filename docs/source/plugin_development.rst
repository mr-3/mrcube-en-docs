プラグイン開発
==============

.. contents:: コンテンツ 
   :depth: 2
   
MR\ :sup:`3` \のプラグイン作成に関するクラス(org.semanticweb.mmm.mr3.plugin.MR3Pluginクラス)及びプラグインの作成方法について説明する．また，プラグインのサンプルを示す．

MR\ :sup:`3` \Pluginクラス
--------------------------
org.semanticweb.mmm.mr3.plugin.MR3Pluginクラス(以下，MR3Pluginクラス)は，abstract public void exec()抽象メソッドをもつ抽象クラスである．MR\ :sup:`3` \のプラグインを作成するには，MR3Pluginクラスを継承して，execメソッドをオーバーライドする．MR3Pluginクラスは，ユーティリティメソッドを提供する．プラグイン作成者は，MR3Pluginクラスが提供するユーティリティメソッドを用いることで，Jenaが提供するcom.hp.hpl.mesa.rdf.jena.model.Modelインタフェース(以下，Model)からMR\ :sup:`3` \のグラフへの変換とMR\ :sup:`3` \のグラフからJenaのModelを得ることが可能となる．以下に，ユーティリティメソッドを示す．(JavaDoc MR3Plugin)

protected JDesktopPane getDesktopPane()
    JDesktopPaneを得る．内部ウィンドウを作成する際に用いる．
protected void replaceRDFModel(Model model)
    Jenaが提供するModelを，MR\ :sup:`3` \のRDFグラフへ変換する．変換したRDFグラフを編集中のRDFグラフと置換する．
protected void mergeRDFModel(Model model)
    Jenaが提供するModelを，MR\ :sup:`3` \のRDFグラフへ変換する．変換したRDFグラフを編集中のRDFグラフにマージする．
protected void mergeRDFSModel(Model model)
    Jenaが提供するModelを，MR\ :sup:`3` \のRDFSグラフへ変換する．変換したRDFSグラフを編集中のRDFSグラフにマージする．
protected void replaceProjectModel(Model model)
    Jenaが提供するModelを，MR^3のプロジェクトへ変換する．引数のModelは，MR^3のプロジェクトファイル．
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

以下に，MR\ :sup:`3` \のプラグインの実例を示す．ここで示すプラグインは，MR\ :sup:`3` \に含まれている．

マニフェストファイル
~~~~~~~~~~~~~~~~~~~~

.. code-block:: mf

    Manifest-Version: 1.0
    
    Name: org.semanticweb.mmm.mr3.sample.ReplaceRDFModelSample.class
    menu-name: ReplaceRDFModelSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: Replace RDF Model Sample Program. 
    
    Name: org.semanticweb.mmm.mr3.sample.GetRDFModelSample.class
    plugin-name: GetRDFModelSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: Get RDF Model Sample Program.
    
    Name: org.semanticweb.mmm.mr3.sample.OpenProjectSample.class
    plugin-name: OpenProjectSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: Open Project File Sample Program.
    
    Name: org.semanticweb.mmm.mr3.sample.SelectNodesSample.class
    plugin-name: SelectNodesSample
    creator: Takeshi Morita
    date: 2004-01-24
    description: This plugin select mr3:a, mr3:b and mr3:c nodes.
    
    Name: org.semanticweb.mmm.mr3.sample.GroupNodesSample.class
    plugin-name: GroupNodesSample
    creator: Takeshi Morita
    date: 2003-12-23
    description: This plugin group mr3:a, mr3:b and mr3:c nodes.
    
    Name: org.semanticweb.mmm.mr3.layoutPlugin.SugiyamaLayoutPlugin.class
    plugin-name: SugiyamaLayout
    creator: Takeshi Morita
    date: 2004-01-24
    description: This is layout plugin sample program.
    
    Name: org.semanticweb.mmm.mr3.owlPlugin.OWLImportPlugin.class
    menu-name: OWLImportPlugin
    creator: Takeshi Morita
    date: 2004-01-24
    description: This is owl import plugin.
    
    
サンプルプラグイン１
~~~~~~~~~~~~~~~~~~~~

サンプルプラグイン１では，subjectがhttp://mr3.sample.resource，predicateがhttp://mr3.sample.property，objectがSampleであるStatementから，JenaのModelを作成する．MR3PluginクラスのreplaceRDFModeメソッドを用いて，作成したJenaのModelをMR3のRDFグラフへ変換する．以下は，サンプルプラグイン１のソースコードである．

.. code-block:: java

    /*
     * @(#) SamplePlugin1.java
     */
     
    package org.semanticweb.mmm.mr3.sample;
    
    import org.semanticweb.mmm.mr3.plugin.*;
    import com.hp.hpl.jena.rdf.model.*;
    import com.hp.hpl.jena.vocabulary.*;
    
    /**
     * @author Takeshi Morita
     * replace RDF Model Sample
     */
    public class SamplePlugin1 extends MR3Plugin {
    
    	public void exec() {
    		Model sampleModel = ModelFactory.createDefaultModel();
    		try {
    			String sampleURI = "http://mmm.semanticweb.org/mr3#";
    			Resource sampleSubject =  ResourceFactory.createResource(sampleURI+"sample_subject");
    			Property sampleProperty = ResourceFactory.createProperty(sampleURI+"sample_property");
    			Literal sampleLiteral = sampleModel.createLiteral("sample_literal");
    			Statement stmt = sampleModel.createStatement(sampleSubject, sampleProperty, sampleLiteral);
    			sampleModel.add(stmt);
    			Resource sampleSubjectType =  ResourceFactory.createResource(sampleURI+"sample_subjectType");
    			stmt = sampleModel.createStatement(sampleSubject, RDF.type, sampleSubjectType);
    			sampleModel.add(stmt);
    		} catch (RDFException e) {
    	   		e.printStackTrace();
    		}
            replaceRDFModel(sampleModel);
    	}
    }   

サンプルプラグイン２
~~~~~~~~~~~~~~~~~~~~

サンプルプラグイン２では，MR\ :sup:`3` \PluginクラスのgetRDFModelメソッドを用いてMR\ :sup:`3` \のRDFグラフからJenaのModelを獲得する．獲得したModelをRDFに変換して内部ウィンドウに出力する．以下は，サンプルプラグイン２のソースコードである．

.. code-block:: java

    /*
     * @(#) SamplePlugin2.java
     */
     
    package org.semanticweb.mmm.mr3.sample;
    
    import java.awt.*;
    import java.io.*;
    import javax.swing.*;
    import javax.swing.event.*;
    import org.semanticweb.mmm.mr3.plugin.*;
    import com.hp.hpl.jena.rdf.model.*;
    
    public class SamplePlugin2 extends MR3Plugin {
    
    	private JTextArea textArea;
    	private JInternalFrame srcFrame;
        
    	public SamplePlugin2() {
    		textArea = new JTextArea();
    		initSRCFrame();
    		srcFrame.getContentPane().add(textArea);
    	}
        
	   private void initSRCFrame() {
    		srcFrame = new JInternalFrame("Sample Plugin 2", true, true);
    		srcFrame.addInternalFrameListener(new InternalFrameAdapter() {
    			public void internalFrameClosing(InternalFrameEvent e) {
    	   			srcFrame.setVisible(false);
    			}
    		});
    		srcFrame.setDefaultCloseOperation(WindowConstants.DO_NOTHING_ON_CLOSE);
    		srcFrame.setBounds(new Rectangle(100, 100, 450, 300));
    	}
        
    	public void exec() {
    		getDesktopPane().add(srcFrame);
    		srcFrame.setVisible(true);
    		try {
    			Model rdfModel = getRDFModel();
    			Writer out = new StringWriter();
    			rdfModel.write(new PrintWriter(out));
    			textArea.setText(out.toString());
    		} catch (RDFException e) {
	       		e.printStackTrace();
	       	}
    	}
    }

SugiyamaLayoutPlugin
~~~~~~~~~~~~~~~~~~~~

SugiyamaLayoutPluginは，JGraphpadに付属するSugiyamaLayoutAlgorithm.javaをMR\ :sup:`3` \用に修正したクラスを利用して作成したプラグインである．SugiyamaLayoutAlgorithmクラスは，performsメソッドをもっている．performsメソッドは，org.jgraph.JGraphを引数にとり，グラフの整形を行う．SugiyamaLayoutPluginでは，MR3PluginクラスのgetRDFGraph，getClassGraph，getPropertyGraphメソッドを利用して，MR\ :sup:`3` \のグラフをJGraphオブジェクトとして受け取り，それをSugiyamaLayoutAlgoritmクラスのperformsメソッドに渡すことで，グラフを整形を行うことができる．以下は，SugiyamaLayoutPluginクラスのソースコードである．

.. code-block:: java

    package org.semanticweb.mmm.mr3.layoutPlugin;
    
    import java.awt.*;
    import org.semanticweb.mmm.mr3.plugin.*;
    import org.jgraph.*;
    
    public class SugiyamaLayoutPlugin extends MR3Plugin {
    
    	public void applySugiyamaLayout(JGraph graph, Point space) {
    		SugiyamaLayoutAlgorithm sugiyamaLayout = new SugiyamaLayoutAlgorithm();
    		sugiyamaLayout.perform(graph, true, space);
    	}
        
    	public void exec() {
    		applySugiyamaLayout(getRDFGraph(), new Point(200, 200));
            
    		reverseClassArc();
    		applySugiyamaLayout(getClassGraph(), new Point(200, 200));
    		reverseClassArc();
            
    		reversePropertyArc();
    		applySugiyamaLayout(getPropertyGraph(), new Point(200, 200));
    		reversePropertyArc();
    	}
    }

TODO
----
* 現状の実装状況に合わせて，ドキュメントを修正する
