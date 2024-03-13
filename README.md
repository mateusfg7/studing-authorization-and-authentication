# Studing Authentication and Authorization
Repo with my studies about Authentication and Authorization of users and resources

## Roadmap

- [ ] Plan app and do relations
- [ ] Setup Nest.js
- [ ] Setup Database
- [ ] Add basic routes and actions
- [ ] Setup authentication
  - [ ] Setup JWT
- [ ] Setup authorization
- [ ] Create Front-end

## Rules&Features
The example project will be a micro-blogging app, like Twitter/X. The authentication will be a simple user-password redentials.

### Entities&Relations
- **`User`**
  - User ID [unique|uuid]
  - Name
  - Email [unique]
  - Password
  - Username [unique]
  - Description Markdown
  - Picture
  - Role [enum = "root", "admin", "moderator", "member"]
  - Private [boolean]
  - Ban Status [enum = "active", "banned"]
  - Created at
  - Updated at
  - **Relations**
      - A `User` CREATE many `Post`s
      - A `User` CREATE many `Reply`s
      - Many `User`s FOLLOW many `User`s
- **`Post`**
  - Title
  - Content Markdown
  - Edited [boolean]
  - Created at
  - Updated at
  - **Relations**
    - Many `Post`s IS CREATED by a `User`
    - A `Post` HAVE many `Reply`s
- **`Reply`**
  - Content Markdown
  - Edited [boolean]
  - Created at
  - Updated at
  - **Relations**
    - Many `Reply`s IS CREATED by a `User`
    - Many `Reply`s IS FROM a `Post` or another `Reply`
- _under construction..._

### Features
- Create user
- Post new content
- Reply a post
- Edit post
- Edit reply
- Delete content
- Update profile info
  - Picture
  - Description
  - Email
  - Username
  - Password
#### Role Rules
**Root**
1. Can't be deleted after creation, is the first user created.
2. Can do anything as long as it doesn't contradict the previous rules
**Admin**: 
1. Can add/remove "moderetor" role
2. Can't add/remove "admin" role
3. Can do anything as long as it doesn't contradict the previous rules.
**Moderator**: 
