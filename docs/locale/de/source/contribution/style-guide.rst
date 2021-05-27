################################
Styleguide für die Dokumentation
################################

Dieser Abschnitt beschreibt die Stilvorgaben für das Schreiben der Dokumentation. 
Er basiert auf dem Sphinx-basierten Dokumentations-Styleguide.

**********
Dateinamen
**********

Verwenden Sie nur Kleinbuchstaben und das Symbol - (Minus).

*************************
Whitespaces (Leerzeichen)
*************************

Einrückung
==========

Einrücken mit 2 Leerzeichen.

Except:

* ``toctree`` direktive erfordert eine Einrückung mit 3 Leerzeichen.

Leerzeilen
===========

Eine Leerzeile vor jedem Abschnitt (z. B. H1, H2, ...).
Siehe `Überschriften`_ für ein Beispiel.

Eine Leerzeile zur Trennung von Direktiven.

.. code-block:: rst

  Some text before.

  .. note::

    Some note.

    Ausnahme: Direktiven können ohne Leerzeilen geschrieben werden, 
    wenn sie nur eine Zeile lang sind.

.. code-block:: rst

  .. note:: A short note.


***********
Zeilenlänge
***********

Die Maximale Zeilenläge beträgt 145 Zeichen.

*************
Überschriften
*************

Use the following symbols to create headings:

#. ``#`` with overline
#. ``*`` with overline
#. ``=``
#. ``-``
#. ``^``
#. ``"``

Beispiel: 

.. code-block:: rst

  ##################
  H1: document title
  ##################

  Introduction text.


  *********
  Sample H2
  *********

  Sample content.


  **********
  Another H2
  **********

  Sample H3
  =========

  Sample H4
  ---------

  Sample H5
  ^^^^^^^^^

  Sample H6
  """""""""

  And some text.

  Wenn Sie mehr als die Überschriftsebene 4 (d. h. H5 oder H6) benötigen, sollten Sie ein neues Dokument erstellen.

  In einem Dokument sollte es nur eine H1 geben. 

.. note::

  See also `Sphinx's documentation about sections`_.


***********
Code-Blöcke
***********

Verwenden Sie die Direktive code-block **und** geben Sie die Programmiersprache an. 
Als Beispiel:

.. code-block:: rst

  .. code-block:: python

    import this

********************
Links und Referenzen
********************

Verwenden Sie Fußnoten für Links und Referenzen mit der Direktive ``target-notes``.
Als Beispiel:


.. code-block:: rst

  #############
  Some document
  #############

  Some text which includes links to `Example website`_ and many other links.

  `Example website`_ can be referenced multiple times.

  (... document content...)

  And at the end of the document...

  ********
  Verweise
  ********

  .. target-notes::

  .. _`Example website`: http://www.example.com/


**********
References
**********

.. target-notes::

.. _`Sphinx's documentation about sections`:
   http://sphinx.pocoo.org/rest.html#sections