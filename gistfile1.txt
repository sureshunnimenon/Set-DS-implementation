var mySet = function(){
  var collection = [];
  
  // method to test whether element exists
  this.has = function(element){
    return (collection.indexOf(element) !== -1)
  };
  
  // method to return all elements of set 
  this.values = function(){
    return collection;
  };
  
  // method to add an element to the set
  this.add = function(element){
    if(!this.has(element)){
      collection.push(element);
      return true;
    }
    else{
      return false;
    }
  };
  
  //method to remove an element from set 
  this.remove = function(element){
    if(!this.has(element)){
      var index=collection.indexOf(element);
      collection.splice(index,1);
      return true;
    }
    else
      {
        return false;
      }
  };
  
  //method to return size of collection
  this.size = function(){
    return collection. length;
  }
 //method to union two sets
  this.union=function(otherSet){
    var unionSet = new mySet();
    var firstSet = this.values();
    var secondSet = otherSet.values();
    
    firstSet.forEach(function(e){
                     unionSet.add(e);
                     });
    secondSet.forEach(function(e){
                      unionSet.add(e);
                      });
    return unionSet;
  }
  
  //method to return intersection of two sets as a new set
  this.interSection = function(otherSet){
      var interSet = new mySet();
    
      var firstSet = this.values();
      firstSet.forEach(function(e){
        if(otherSet.has(e)){
          interSet.add(e);
        }
      });
    return interSet;  
  };
  
//method to return difference of two sets 
  this.difference = function(otherSet){
    var differenceSet = new mySet();
    var firstSet = this.values();
    firstSet.forEach(function(e){
      if(!otherSet.has(e)){
        differenceSet.add(e);
      }
    });
    return differenceSet;
  }
  
  //method to test if the passed set is set set of the main set
  this.subset = function(otherSet){
    var firstSet = this.values;
    return firstSet.every(function(e){
      return otherSet.has(e);
    })
  }
}