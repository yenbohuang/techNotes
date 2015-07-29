# General Mongo DB Shell Method Notes

## Create Index

Single index

```
   db.yourCollection.createIndex( { columnA: 1 } )
```

Compound index

```
   db.yourCollection.createIndex( { columnA: 1, columnB: -1 } )
```

Unique index

```
   db.yourCollection.createIndex( { columnA: 1 }, {unique: true} )
```
