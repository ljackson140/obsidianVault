Notes:
- API works fine 
- Refactoring is more of the frontend 

2 Tables: 
- Parent => TrackingComments → Seeded data
- Parent => DisciplineTrackingComment → stores all tracking comments when you add 1 
- Child =>  DisciplineInternalTrackingComments → no idea 
- Child => TrackingCommentNotes → stores notes of tracking comment 

Current behavior:
- Pre-populates table when adding 1 tracking comments
- IsChecked flag determines if they have been added or removed (1 => added, 0 => Not added) 

Future behavior:
- No pre-populating data
- Still sending a list to the backend 

- [x] Remove IsCheck Property
- [x] Add a duplicate/single Tracking Comment 
- [ ] Selected MenuItem Adds a new 