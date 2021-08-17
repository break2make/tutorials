MongoDB
===


# Mongoengine in Python

`flask-mongoengine` has api for pagination, but those are not available in mongoengine yet. However, there are api like (skip() and limit()), which can be used to implement the pagination as given below ([source](https://www.codegrepper.com/code-examples/whatever/mongoengine+pagination)):

```   
 def skiplimit(page_size, page_num):
        """returns a set of documents belonging to page number `page_num`
        where size of each page is `page_size`.
        """
        # Calculate number of documents to skip
        skips = page_size * (page_num - 1)

        # Skip and limit
        cursor = db['students'].find().skip(skips).limit(page_size)

        # Return documents
        return [x for x in cursor]
```
