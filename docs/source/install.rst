Installation
============

.. contents:: Contents
   :depth: 2


Requirements
------------
MR\ :sup:`3` \ is implemented by Java language. JRE (Java Runtime Environment) 18 or later is required to execute. In ver. 22.5.2, JRE 18 is embedded, so there is no need to install a JRE.

We confirmed MR\ :sup:`3` \ following environemnt.

* MS Windows 11 + openjdk version "18.0.1.1"
* macOS 14.4.1 + openjdk version "18.0.1.1" 

How to Install
--------------
Windows
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
#. Download **mrcube-22.5.2.msi** from the `download page <https://github.com/mr-3/mrcube/releases>`_ and open the file.
#. The message "Your PC has been protected by Windows" is displayed, click on the "More information" link.
#. Click the 'Run' button.
#. 'Do you want to allow apps from this unknown publisher to make changes to the device?' is displayed in the dialog box. Then, Click 'Yes'.
#. Run the shortcut that is created on the desktop.

macOS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
#. Download and extract **mrcube-22.5.2-x64.dmg** from the `download page <https://github.com/mr-3/mrcube/releases>`_ and copy **mrcube-22.5.2.app** to the 'Applications' folder.
#. Run **mrcube-22.5.2.app**.
#. The message "mrcube-22.5.2 is an application downloaded from the Internet. Are you sure you want to open it?" Click the "Open" button.


How to Uninstall
----------------
Windows
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Select the Apps menu from the Settings screen, select **mrcube-22.5.2** from the list of installed apps and uninstall it.

macOS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Delete **mrcube-22.5.2.app** from the applications folder.


Used libraries
--------------
MR\ :sup:`3` \ uses the following libraries: 

* `FlatLaf - Flat Look and Feel <https://www.formdev.com/flatlaf/>`_ (`License <http://www.apache.org/licenses/LICENSE-2.0>`__)
* `JGraph and JGraphAddons <http://www.jgraph.com/>`_ (`License <https://github.com/jgraph/legacy-jgraph5/blob/master/LICENSE>`__)
* `Apache Jena <https://jena.apache.org/>`_ (`License <http://www.apache.org/licenses/LICENSE-2.0>`__) 
* `Apache Batik SVG Toolkit <https://xmlgraphics.apache.org/batik/>`_ (`License <https://xmlgraphics.apache.org/batik/license.html>`__)
* `Drawing Graphs with VGJ <http://www.eng.auburn.edu/department/cse/research/graph_drawing/graph_drawing.html>`_ (`License <http://www.eng.auburn.edu/department/cse/research/graph_drawing/COPYING>`__)
* `Material Design icons by Google <https://github.com/google/material-design-icons>`_ (`License <https://www.apache.org/licenses/LICENSE-2.0.txt>`__)