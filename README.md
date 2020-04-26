# Hash_Tables_Data_Structure


> ## hash function: :cry: 
``` js
function hash(key, arrayLen) {
  let total = 0;
  for (let char of key) {
    // map "a" to 1, "b" to 2, "c" to 3, etc.
    let value = char.charCodeAt(0) - 96
    total = (total + value) % arrayLen;
  }
  return total;
}
```

> ## hash function, improved version: :smile:
``` js
function hash(key, arrayLen) {
  let total = 0;
  let WEIRD_PRIME = 31;
  for (let i = 0; i < Math.min(key.length, 100); i++) {
    let char = key[i];
    let value = char.charCodeAt(0) - 96
    total = (total * WEIRD_PRIME + value) % arrayLen;
  }
  return total;
}
```

> ## Hash Table Implementation: :wink:
> hash(), set(), get(), keys(), values()
``` js
class HashTable {
  constructor(size=53){
    this.keyMap = new Array(size);
  }

  _hash(key) {
    let total = 0;
    let WEIRD_PRIME = 31;
    for (let i = 0; i < Math.min(key.length, 100); i++) {
      let char = key[i];
      let value = char.charCodeAt(0) - 96
      total = (total * WEIRD_PRIME + value) % this.keyMap.length;
    }
    return total;
  }
  set(key,value){
    let index = this._hash(key);
    if(!this.keyMap[index]){
      this.keyMap[index] = [];
    }
    this.keyMap[index].push([key, value]);
  }
  get(key){
    let index = this._hash(key);
    if(this.keyMap[index]){
      for(let i = 0; i < this.keyMap[index].length; i++){
        if(this.keyMap[index][i][0] === key) {
          return this.keyMap[index][i][1]
        }
      }
    }
    return undefined;
  }

  keys(){
    let keysArr = [];
    for(let i = 0; i < this.keyMap.length; i++){
      if(this.keyMap[i]){
        for(let j = 0; j < this.keyMap[i].length; j++){
          if(!keysArr.includes(this.keyMap[i][j][0])){
            keysArr.push(this.keyMap[i][j][0])
          }
        }
      }
    }
    return keysArr;
  }

  values(){
    let valuesArr = [];
    for(let i = 0; i < this.keyMap.length; i++){
      if(this.keyMap[i]){
        for(let j = 0; j < this.keyMap[i].length; j++){
          if(!valuesArr.includes(this.keyMap[i][j][1])){
            valuesArr.push(this.keyMap[i][j][1])
          }
        }
      }
    }
    return valuesArr;
  }
}

let ht = new HashTable(17);
ht.set("maroon","#800000")
ht.set("yellow","#FFFF00")
ht.set("olive","#808000")
ht.set("salmon","#FA8072")
ht.set("lightcoral","#F08080")
ht.set("mediumvioletred","#C71585")
ht.set("plum","#DDA0DD")

console.log(ht)
// HashTable {
//   keyMap: [
//     [ [Array] ],
//     <2 empty items>,
//     [ [Array] ],
//     <4 empty items>,
//     [ [Array], [Array] ],
//     <1 empty item>,
//     [ [Array] ],
//     <2 empty items>,
//     [ [Array] ],
//     <2 empty items>,
//     [ [Array] ]
//   ]
// }

console.log(ht.keyMap)
// [
//   [ [ 'plum', '#DDA0DD' ] ],
//   <2 empty items>,
//   [ [ 'salmon', '#FA8072' ] ],
//   <4 empty items>,
//   [ [ 'maroon', '#800000' ], [ 'yellow', '#FFFF00' ] ],
//   <1 empty item>,
//   [ [ 'olive', '#808000' ] ],
//   <2 empty items>,
//   [ [ 'lightcoral', '#F08080' ] ],
//   <2 empty items>,
//   [ [ 'mediumvioletred', '#C71585' ] ]
// ]
console.log(ht.get("maroon")) // #800000
console.log(ht.get("yellow")) // #FFFF00
console.log(ht.get("olive")) // #808000
console.log(ht.get("salmon")) // #FA8072
console.log(ht.get("lightcoral")) // #F08080
console.log(ht.get("mediumvioletred")) // #C71585
console.log(ht.get("plum")) // #DDA0DD

ht.keys().forEach(function(key){
  console.log(ht.get(key));
})
// #DDA0DD
// #FA8072
// #800000
// #FFFF00
// #808000
// #F08080
// #C71585

console.log(ht.values())
// [
//   '#DDA0DD',
//   '#FA8072',
//   '#800000',
//   '#FFFF00',
//   '#808000',
//   '#F08080',
//   '#C71585'
// ]

```
![hashing](https://github.com/NoriKaneshige/Hash_Tables_Data_Structure/blob/master/hashing.png)
![hash_tables](https://github.com/NoriKaneshige/Hash_Tables_Data_Structure/blob/master/hash_tables.png)
![separate_chaining](https://github.com/NoriKaneshige/Hash_Tables_Data_Structure/blob/master/separate_chaining.png)
![linear_probing](https://github.com/NoriKaneshige/Hash_Tables_Data_Structure/blob/master/linear_probing.png)
![hash_tables_set_get](https://github.com/NoriKaneshige/Hash_Tables_Data_Structure/blob/master/hash_tables_set_get.png)
![hash_tables_keys_values](https://github.com/NoriKaneshige/Hash_Tables_Data_Structure/blob/master/hash_tables_keys_values.png)
![hash_tables_bigO](https://github.com/NoriKaneshige/Hash_Tables_Data_Structure/blob/master/hash_tables_bigO.png)


