For sending SMS mailings, you of course need to have the mobile numbers
of the people you want to reach. SMS (or mobile phone) numbers are
stored in a field specially designed for this. Also you need to
authorize the selection(s) you send your mailing(s) to.

### 1. Store numbers in mobile phone field

For storing mobile phone numbers you use a database or collection field
of type **Phone -\> SMS**

Go to *Profiles \> Database Management \>* [Edit
fields](./database-and-collection-field-types.md)
to configure the field settings of your database or collections

![](../images/telefoonveld-sms.png)

### 2. Authorize selection for mass mailings with SMS

At each selection or miniselection that you want to target a mailing to,
you must indicate that it may be used for such a mailing. This way you
prevent that a mailing is accidentaly sent to the wrong selection (and
thus to the wrong people).

To authorize the selection of mini selection go to *Profiles -\>
Database management -\>* [Set
intentions](./database-intentions-enabling-the-target-for-mass-mailings.md).
Choose the selection that you want to use, and then **check the box**for
**SMS mailings**.

Well, that's all ya need to know.
