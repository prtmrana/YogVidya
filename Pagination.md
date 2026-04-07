<p><a target="_blank" href="https://app.eraser.io/workspace/EFkIziz3z26cfVpkPIYU" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

---

-getting the data in chunks instead of whole 

- [ ] Advantages : 
-   Improve performance
-   Fast API response 
-   Better UI experience 
> Classes & Interfaces used in Pagination :

1. Pageable
- Interface that contain : page number , page size ,sorting
2 . PageRequest

-  It is a implementation class of pageable 
- .of()  method is static method inside PageRequest class to create the object of PageRequest which implements Pageable.(constructor is not public in class thats why static method is there)
- `Pageable pageable = PageRequest.of(page, size);` 
- [ ] page is chunk of data we want (it is 0 based index)  page 0 means first page and page 1 means second.
- [ ] size means how many records per page we want.
- [ ] `?page=1&size=3` : Give me 2 page with 3 records per page
- [ ] internally : `SELECT * FROM user LIMIT 3 OFFSET 3;`   `OFFSET = page × size` 


3 . Sort

-  it is a spring data class 
- used to specify sorting rules like ascending or descending on one or more fields when fetching data from the database.
- `﻿Sort sort = direction.equalsIgnoreCase("asc")
        ? Sort.by(sortBy).ascending()
        : Sort.by(sortBy).descending();` 
- direction we pass from controller  like asc or desc
- sortBy : column on which sorting we want
- `Pageable pageable = PageRequest.of(page, size, sort);` : it is static overloaded method


1. `Page<User> findByName(String name, Pageable pageable);  ` Spring adds LIMIT ,OFFSET,ORDERBY(if sorting added in pageable.
2. `userRepo.findByName(name);` : just find where name =?
4 . Page 

-  is an interface in Spring Data
- that represents a paginated result from the database.
- `Page {
 content = [User1, User2, User3]
 totalElements = 10
 totalPages = 4
 currentPage = 1
 size = 3
}` 




<!--- Eraser file: https://app.eraser.io/workspace/EFkIziz3z26cfVpkPIYU --->