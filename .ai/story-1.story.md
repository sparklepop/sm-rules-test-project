# Story 1: Basic Blog Setup and Post Management

**Status**: draft  
**Type**: feature  
**Priority**: high  
**Epic**: MVP  

## Description
Set up the basic Rails application with PostgreSQL and implement the core Post model with CRUD operations. This will provide the foundation for the blog platform.

## Acceptance Criteria
1. Rails application is set up with PostgreSQL
2. Post model exists with:
   - title (string, required)
   - content (text, required)
   - status (enum: published/archived, default: published)
3. Basic CRUD operations for posts:
   - View all posts (index)
   - View single post (show)
   - Create new post (new/create)
   - Archive post (update status)
4. Simple, responsive UI using vanilla JavaScript
5. Basic HTTP authentication for post management
6. All tests passing with minimum 90% coverage
7. Documentation updated

## Technical Notes
- Use Rails 8.x
- PostgreSQL 14+
- Vanilla JavaScript for frontend interactions
- RSpec for testing
- Basic HTTP authentication (username/password in credentials)

## Subtasks
- [ ] Initialize new Rails application
- [ ] Configure PostgreSQL database
- [ ] Create Post model with migrations
- [ ] Implement PostsController with CRUD actions
- [ ] Create basic views (index, show, new, edit forms)
- [ ] Add vanilla JavaScript for interactive features
- [ ] Implement basic HTTP authentication
- [ ] Write model and controller tests
- [ ] Add system tests for critical paths
- [ ] Update documentation

## Implementation Details
```ruby
# Post Model Schema
create_table :posts do |t|
  t.string :title, null: false
  t.text :content, null: false
  t.string :status, null: false, default: 'published'
  t.timestamps
end

# Post Model
class Post < ApplicationRecord
  validates :title, presence: true
  validates :content, presence: true
  validates :status, inclusion: { in: %w[published archived] }
  
  scope :published, -> { where(status: 'published') }
  scope :archived, -> { where(status: 'archived') }
end
```

## Test Cases
1. Model Tests:
   - Validates required fields
   - Validates status values
   - Scopes work correctly
2. Controller Tests:
   - CRUD operations work
   - Authentication required for management
3. System Tests:
   - Can view posts without auth
   - Can manage posts with auth
   - Archive functionality works

## Dependencies
- Ruby 3.x
- Rails 7.x
- PostgreSQL 14+
- RSpec Rails
- Factory Bot Rails

## Risks
- None identified for basic setup

## Time Estimate
- 1-2 days

## Chat Log
- Initial story created 