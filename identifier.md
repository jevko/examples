# Structured identifier with metadata

A structured identifier with metadata encoded with Jevko:

```
id[
  worker[32]
  provider[
    group[5]
    SomeProvider
  ]
  123
]
```

an XML equivalent:

```
<id>
  <worker>32</worker>
  <provider>
    <group>5</group>
    SomeProvider
  </provider>
  123
</id>
```