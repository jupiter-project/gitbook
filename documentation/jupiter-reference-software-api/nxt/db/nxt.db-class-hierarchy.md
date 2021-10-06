# nxt.db Class Hierarchy

[Skip navigation links](nxt.db-class-hierarchy.md#skip.navbar.top)

* [Overview](../../overview.md)
* [Package](nxt.db.md)
* Class
* Tree
* [Deprecated]()
* [Index](../../index-files/a-index.md)
* [Help](../../how-this-api-document-is-organized.md)
* [Prev](../crypto/nxt.crypto-class-hierarchy.md)
* [Next](../env/nxt.env-class-hierarchy.md)
* [Frames](https://jpr4.gojupiter.tech/doc/index.html?nxt/db/package-tree.html)
* [No Frames](nxt.db-class-hierarchy.md)
* [All Classes](../../all-classes.md)

## Hierarchy For Package nxt.db

Package Hierarchies:

* [All Packages](../../class-hierarchy.md)

### Class Hierarchy

* java.lang.Object
  * nxt.db.[BasicDb](https://jpr4.gojupiter.tech/doc/nxt/db/BasicDb.html)
    * nxt.db.[TransactionalDb](https://jpr4.gojupiter.tech/doc/nxt/db/TransactionalDb.html)
  * nxt.db.[BasicDb.DbProperties](https://jpr4.gojupiter.tech/doc/nxt/db/BasicDb.DbProperties.html)
  * nxt.db.[DbClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.html)
    * nxt.db.[DbClause.BooleanClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.BooleanClause.html)
    * nxt.db.[DbClause.ByteClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.ByteClause.html)
    * nxt.db.[DbClause.FixedClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.FixedClause.html)
    * nxt.db.[DbClause.IntClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.IntClause.html)
    * nxt.db.[DbClause.LikeBothClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.LikeBothClause.html)
    * nxt.db.[DbClause.LikeClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.LikeClause.html)
    * nxt.db.[DbClause.LongClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.LongClause.html)
    * nxt.db.[DbClause.NotNullClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.NotNullClause.html)
    * nxt.db.[DbClause.NullClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.NullClause.html)
    * nxt.db.[DbClause.StringClause](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.StringClause.html)
  * nxt.db.[DbIterator](https://jpr4.gojupiter.tech/doc/nxt/db/DbIterator.html) \(implements java.lang.AutoCloseable, java.lang.Iterable, java.util.Iterator\)
  * nxt.db.[DbKey.Factory](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.Factory.html)
    * nxt.db.[DbKey.LinkKeyFactory](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.LinkKeyFactory.html)
    * nxt.db.[DbKey.LongKeyFactory](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.LongKeyFactory.html)
    * nxt.db.[DbKey.StringKeyFactory](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.StringKeyFactory.html)
  * nxt.db.[DbKey.LinkKey](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.LinkKey.html) \(implements nxt.db.[DbKey](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.html)\)
  * nxt.db.[DbKey.LongKey](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.LongKey.html) \(implements nxt.db.[DbKey](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.html)\)
  * nxt.db.[DbKey.StringKey](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.StringKey.html) \(implements nxt.db.[DbKey](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.html)\)
  * nxt.db.[DbUtils](https://jpr4.gojupiter.tech/doc/nxt/db/DbUtils.html)
  * nxt.db.[DbVersion](https://jpr4.gojupiter.tech/doc/nxt/db/DbVersion.html)
  * nxt.db.[DerivedDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/DerivedDbTable.html)
    * nxt.db.[EntityDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/EntityDbTable.html)
      * nxt.db.[PersistentDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/PersistentDbTable.html)
        * nxt.db.[PrunableDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/PrunableDbTable.html)
          * nxt.db.[VersionedPrunableDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/VersionedPrunableDbTable.html)
            * nxt.db.[VersionedPersistentDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/VersionedPersistentDbTable.html)
      * nxt.db.[VersionedEntityDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/VersionedEntityDbTable.html)
    * nxt.db.[ValuesDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/ValuesDbTable.html)
      * nxt.db.[VersionedValuesDbTable](https://jpr4.gojupiter.tech/doc/nxt/db/VersionedValuesDbTable.html)
  * nxt.db.[FilteredConnection](https://jpr4.gojupiter.tech/doc/nxt/db/FilteredConnection.html) \(implements java.sql.Connection\)
  * nxt.db.[FilteredStatement](https://jpr4.gojupiter.tech/doc/nxt/db/FilteredStatement.html) \(implements java.sql.Statement\)
    * nxt.db.[FilteredPreparedStatement](https://jpr4.gojupiter.tech/doc/nxt/db/FilteredPreparedStatement.html) \(implements java.sql.PreparedStatement\)
  * nxt.db.[FilteringIterator](https://jpr4.gojupiter.tech/doc/nxt/db/FilteringIterator.html) \(implements java.lang.AutoCloseable, java.lang.Iterable, java.util.Iterator\)
  * nxt.db.[FullTextTrigger](https://jpr4.gojupiter.tech/doc/nxt/db/FullTextTrigger.html) \(implements nxt.db.[TransactionalDb.TransactionCallback](https://jpr4.gojupiter.tech/doc/nxt/db/TransactionalDb.TransactionCallback.html), org.h2.api.Trigger\)

### Interface Hierarchy

* nxt.db.[DbIterator.ResultSetReader](https://jpr4.gojupiter.tech/doc/nxt/db/DbIterator.ResultSetReader.html)
* nxt.db.[DbKey](https://jpr4.gojupiter.tech/doc/nxt/db/DbKey.html)
* nxt.db.[FilteredFactory](https://jpr4.gojupiter.tech/doc/nxt/db/FilteredFactory.html)
* nxt.db.[TransactionalDb.TransactionCallback](https://jpr4.gojupiter.tech/doc/nxt/db/TransactionalDb.TransactionCallback.html)

### Enum Hierarchy

* java.lang.Object
  * java.lang.Enum \(implements java.lang.Comparable, java.io.Serializable\)
    * nxt.db.[DbClause.Op](https://jpr4.gojupiter.tech/doc/nxt/db/DbClause.Op.html)

[Skip navigation links](nxt.db-class-hierarchy.md#skip.navbar.bottom)

* [Overview](../../overview.md)
* [Package](nxt.db.md)
* Class
* Tree
* [Deprecated]()
* [Index](../../index-files/a-index.md)
* [Help](../../how-this-api-document-is-organized.md)
* [Prev](../crypto/nxt.crypto-class-hierarchy.md)
* [Next](../env/nxt.env-class-hierarchy.md)
* [Frames](https://jpr4.gojupiter.tech/doc/index.html?nxt/db/package-tree.html)
* [No Frames](nxt.db-class-hierarchy.md)
* [All Classes](../../all-classes.md)

