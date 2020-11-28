---
description: >-
  One of the most powerful features of MyBatis has always been its Dynamic SQL
  capabilities.
---

# Dynamic SQL

## if

```markup
<select id="findActiveBlogWithTitleLike"
     resultType="Blog">
  SELECT * FROM BLOG
  WHERE state = ‘ACTIVE’
  <if test="title != null">
    AND title like #{title}
  </if>
</select>
```

```java
@Select({"<script>",
      "SELECT * FROM BLOG WHERE state = 'ACTIVE'",
      "  <if test="title != null">",
      "    AND title like #{title}",
      "  </if>",
      "</script>"})
List<Blog> findActiveBlogWithTitleLike(String title);
```

## choose, when, otherwise

```java
@Update({"<script>",
      "update Author",
      "  <set>",
      "    <if test='username != null'>username=#{username},</if>",
      "    <if test='password != null'>password=#{password},</if>",
      "    <if test='email != null'>email=#{email},</if>",
      "    <if test='bio != null'>bio=#{bio}</if>",
      "  </set>",
      "where id=#{id}",
      "</script>"})
    void updateAuthorValues(Author author);
```
