TEST-FIXES TODO LIST
====================

| [ ] plone.app.caching (tisto)
| [ ] plone.app.contentlisting
| [ ] plone.app.layout
| [ ] plone.app.theming (maartenkling)
| [ ] plone.app.users
| [ ] plone.app.versioningbehavior


DONE
----

| [X] Products.CMFPlacefulWorkflow (tisto)
| [X] Products.CMFPlone
| [X] Products.TinyMCE (excluded from tests)
| [X] collective.elephantvocabulary (tisto)
| [X] grokcore.security (davisagli)
| [X] plone.app.content (tisto)
| [X] plone.app.controlpanel (davisagli)
| [X] plone.app.dexterity (davisagli)
| [X] plone.app.discussion (tisto)
| [X] plone.app.intid (tisto)
| [X] plone.app.portlets (thet)
| [X] plone.app.redirector (tisto)
| [X] plone.app.uuid (tisto)
| [X] plone.dexterity (davisagli)
| [X] plone.formwidget.datetime (thet)
| [X] plone.formwidget.recurrence (thet)
| [X] plone.portlet.collection (tisto)
| [X] plonetheme.sunburst (thet)
| [X] zope.testing/zc.relation (tisto)


How To Fix
==========

plone.app.contenttypes fixture
------------------------------

setup.py::

    extras_require={
        'test': [
            'plone.app.contenttypes',
        ]
    }

testing.py::

    from plone.app.contenttypes.testing import PLONE_APP_CONTENTTYPES_FIXTURE

    class PloneAppDiscussion(PloneSandboxLayer):

        defaultBases = (PLONE_APP_CONTENTTYPES_FIXTURE,)


dexterity
---------

setup.py::

    extras_require={
        'test': [
            'dexterity',
        ]
    }

testing.py::

    from plone.dexterity.fti import DexterityFTI

    def setUpPlone(self, portal):
        fti = DexterityFTI('Document')
        types_tool = getToolByName(portal, "portal_types")
        types_tool._setObject('Document', fti)
