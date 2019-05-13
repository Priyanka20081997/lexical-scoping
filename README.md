# lexical-scoping
## to write a pair of functions viz "makeCacheMatrix" & "cacheSolve" that cache the
## inverse of a matrix

## define makeCacheMatrix as a function which creates object("matrix") that can 
## cache its inverse for the input(an invertible square matrix)

makeCacheMatrix <- function(x = matrix()) {
  inv<- NULL
  set<-function(y){
    x<<- NULL
  }
  get<- function() x
  setinv<- function(inverse) inv<<- inverse
  getin<- function() inv
  list(set = set, get= get,setinv= setinv, getinv=getinv )

}


## cacheSolve is a function which computes the inverse of the special "matrix" 
## returned by makeCacheMatrix above. If the inverse has already been calculated 
## (and the matrix has not changed), then the cachesolve should retrieve the 
## inverse from the cache

cacheSolve <- function(x, ...) {
  
## Return a matrix that is the inverse of 'x'
  
  inv <- x$getinv()
  if(!is.null(inv)) {
    message("getting cached result")
    return(inv)
  }
  data <- x$get()
  inv <- solve(data, ...)
  x$setinv(inv)
  inv
}

