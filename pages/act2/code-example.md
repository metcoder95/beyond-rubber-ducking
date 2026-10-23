---
layout: two-cols
---

# Boilerplate Generation

```javascript
// Repository Layer
class UserRepository {
  async findById(id) {
    return db.query(
      'SELECT * FROM users WHERE id = $1',
      [id]
    );
  }
  // create, update, delete...
}
```

::right::

<div class="pl-4">

```javascript
// Service Layer
class UserService {
  constructor(repository) {
    this.repository = repository;
  }
  
  async getUser(id) {
    const user = await this.repository.findById(id);
    if (!user) throw new Error('User not found');
    return user;
  }
  // createUser, updateUser...
}
```

</div>
