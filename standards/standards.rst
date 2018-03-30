Halium standards
================

Introduction
------------

Halium standards ensure that the Halium community is able to create, iterate, and experiment in a way that remains compatible between Halium ports, distributions, and supporting projects.

Scope
-----

This document contains the requirements and conventions of a Halium standard as well as information for writing and proposing a standard. This information is useful to people who are creating new standards or revising previously accepted standards.

.. _standard-terms-and-conventions:

General terms and conventions
-----------------------------

The following are commonly used terms in the Halium community. To prevent confusion, standards documents should use these terms exactly as they are specified here.

Halium-standard Linux Distribution, HSD
    A Linux (GNU/Linux optionally) software distribution that implements the Halium standards.
HSD root filesystem, HSD rootfs, rootfs
    The file and directory tree that makes up the HSD.
Device
    The computing system targeted by Halium.

Standards documents shall use `IEC verbal forms for expression of provisions`_ to express what is required, recommended, permissive, or possible for implementations of the standard.

All paths listed in a standards document shall assume that the HSD rootfs is the root directory, ``/``.

Standards document format
-------------------------

Standards documents should conform to the following format.

The document shall be written in *valid* ReStructuredText markup for inclusion into this documentation.

Title
^^^^^

The title shall specify the subject covered by the document clearly and concisely.

Introduction
^^^^^^^^^^^^

The introduction shall state the rationale for the document. In other words, the introduction states the problem which the document solves and its method of solving the problem. It shall not contain any provisions.

.. _standard-scope:

Scope
^^^^^

The scope shall specify the people and projects affected by the document's provisions. If it is clear that some groups may be "collaterally" impacted by the provisions, it is required to summarize this impact. The impact summary may be given in the scope or an annex later in the document. If a summary is given in an annex, it is required link to that annex from the scope.

Do not place any provisions in this section.

Terms and definitions
^^^^^^^^^^^^^^^^^^^^^

The terms and definitions section shall follow this format (given here with ReStructuredText markup for convenience):

.. code-block:: ReStructuredText

    Terms and definitions
    ---------------------

    This document follows the general terms, definitions, and expressions defined in the Halium :ref:`standard-terms-and-conventions` with the following additions:

    Additional term
        Term definition.
    [...]
        [...]

Do not place any provisions in this section.

Document body sections
^^^^^^^^^^^^^^^^^^^^^^

Document body sections shall contain the majority of the document's content. This should include all document provisions and example implementations (or links to implementations).

The document body should be organized in the most logical format for its content. This may include the use of multiple subdivision levels and diverse section titles.

Section titles should always be sentence cased. That is, the first letter of the first word should be capitalized and all all other words should be lowercase. Proper nouns are exceptions to this provision.

Annexes
^^^^^^^

Annexes contain information that is potentially interesting to the document's audience but does not fit in the other sections. In particular, annexes:

* Do not specify, but may clarify, document provisions
* May further clarify the reasoning for picking one possible provision over another
* May clarify the effect of provisions on a certain group of people (in addition to the :ref:`standard-scope`)
* May contain other related information that does not fit in the document body

Annexes shall follow the title format "Annex [Letter]: [Short description]". Annex letters will start at the uppercase latin-script letter "A" and continue through the Latin-script alphabet. If more annexes are needed than are available in the alphabet, attach a second letter. Start with the first annex AA, then AB, and so on.

.. _standard-revision:

Revision
^^^^^^^^

The final section of a standards document shall state the version number and changelog of the document. 

Version numbers follow a slight modification of `semantic versioning`_. That is, each section of a MAJOR.MINOR.REVISION version number (such as 1.0.0) conveys different information.

MAJOR version changes indicate that a revision of a standard breaks backwards compatibility. In other words, the functionality or expression changes in the revision render previously standards-abiding projects incompatible with the new standard. Additions or subtractions of required provisions ("shall" provisions) will almost always cause a major version change.

MINOR version changes indicate that the revision adds new provisions but does not break backwards compatibility. Additions or subtractions of any non-required provisions will almost always cause a minor version change.

REVISION version changes indicate that the revision does not add, remove, or change any provision. Revision changes correct spelling, grammar, or markup of previous versions. 

Version number sections shall start as single-digit numbers and increment up by one. This means that 1.9.0 is one minor revision before 1.10.0.

The first accepted version of a standard shall always be version 1.0.0. Documents need not keep a version history before this point.

Documents shall also include a changelog after declaring their version number. This changelog shall contain a summary of the changes in each revision, the new version number that they introduce, the date the changes were drafted (use the date of the final draft), and the date the changes were accepted. The changelog sections shall be sorted in descending order by major, then minor, then revision number.

The following is an example document revision section in ReStructuredText format. Do not deviate from this standard without a very good justification.

.. code-block:: ReStructuredText

    Revision
    --------

    This is version 2.1.0 of the door selling standard. 

    Changelog
    ^^^^^^^^^

    2.1.0
    """""

    Add recommended provision: "Door salesman should warn potential buyers of the safety hazards of French doors."

    Draft date: 2019-03-10
    Acceptance date: 2019-03-10

    2.0.0
    """""

    Remove required provision: "Door salesmen shall always specify French doors as the best possible form of doorway"

    Draft date: 2019-01-10
    Acceptance date: 2019-02-26

    1.0.1
    """""

    Use correct forms of "there" in various sections

    Draft date: 2018-04-15
    Acceptance date: 2018-04-16

    1.0.0
    """""

    This is the first version of the standard.

    Draft date: 2018-03-30 
    Acceptance date: 2018-04-10

Proposing a draft
-----------------

After a draft has been written, it shall be submitted for review before it is accepted. This is called "proposing" the draft.

To propose a draft, the draft author shall make the draft publicly available for viewing. They shall then submit the draft to the Halium community for review.

The most complete way to propose a draft is by creating a Pull Request to `this documentation's GitHub repository`_. This Pull Request is required to add the draft to the repository and include it in the documentation. If the draft author is not comfortable with this workflow, they may file an issue on the repository containing a link to the draft.

The draft should include the version number 1.0.0 and a starting changelog (see :ref:`standard-revision`).

Proposing a revision
--------------------

Proposing a revision to a standard is largely the same process as proposing a draft. The only change is that the proposer shall include the new version number and changelog (see :ref:`standard-revision`).

Draft/revision review
---------------------

Drafts and revisions should be reviewed and corrected for all of the following criteria:

* Drafts shall be free of spelling or grammar errors
* Drafts shall meet the other provisions set in this document
* Provisions in a draft shall be as explicit as possible. They should not leave room for interpretation or questioning of their meaning.
* Provisions in a draft should be reviewed by the projects that they affect. Each participating project shall note if a provision should be contested. Contested provisions should be resolved between the participating projects and the draft author.

If a draft does not meet any of these criteria, the reviewer should mark the problems and submit their review to the proposer. The proposer should then correct the found problems and re-submit the draft for review under the same :ref:`standard-revision`.

Draft/revision acceptance
-------------------------

After a draft or revision has been accepted, its acceptance date shall be noted and it shall be included in the Halium documentation.

Version
-------

This is version 1.0.0 of the Halium Standards standard.

Changelog
^^^^^^^^^

1.0.0
"""""

This is the first version of the standard.

Draft date: 2018-03-30
Acceptance date: 


.. _IEC verbal forms for expression of provisions: http://www.iec.ch/standardsdev/resources/draftingpublications/directives/principles/verbal_forms.htm
.. _semantic versioning: https://semver.org/
.. _this documentation's github repository: https://github.com/halium/docs