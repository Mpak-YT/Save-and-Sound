# SaveAndSound - Use Case Analysis

## Actors

### **Guest (Unauthenticated User)**
A user who is not logged into the system. Can view sounds and the registration page.

### **Registered User**
A logged-in user. Can listen to sounds, create/manage playlists, like sounds.

### **Creator (Content Creator)**
A registered user with the ability to upload, edit, and delete sounds.

### **Admin**
System administrator. Can manage users, sounds, playlists, and view statistics.

## Use Case Scenarios

### **UC1: Register User**

**Actor:** Guest
**Precondition:** User is not logged in and is on the registration page.

**Flow of Events:**
1. User opens the registration page
2. Registration form contains fields: Full Name, Email, Password, Confirm Password, Register button
3. User fills out the form and clicks Register
4. System validates:
   - All required fields are filled
   - Email is in a correct format
   - Password meets complexity requirements (e.g., minimum length, special characters)
   - Password matches confirmation
   - Email is not already registered
5. If validation is successful, a new user is created in the database, and the password is cryptographically hashed
6. System returns success message and redirects to the login page

**Alternative Flows:**
- Email already registered → System displays: "This email is already associated with an account."
- Weak password → System displays: "Password does not meet complexity requirements."
- Other validation errors → Red inline errors under fields

**Postcondition:** New user account is created, and the user can log in.

---

### **UC2: Login**

**Actor:** Guest
**Precondition:** User is on the login page.

**Flow of Events:**
1. User enters email and password, then clicks Login
2. System authenticates the user:
    - The system checks that the email and password match a user in the database.
3. If authentication is successful:
    - The system creates a JWT (JSON Web Token) for the user.
    - The system redirects the user to the main page.
4. If authentication fails:
    - The system displays an error message: "Invalid email or password."

**Alternative Flows:**
- User provides incorrect login credentials → System shows: "Invalid email or password."

**Postcondition:** User is logged in, and the system provides access based on user roles.

---

### **UC3: View Sounds**

**Actor:** Guest / Registered User
**Precondition:** User is on the sounds list page.

**Flow of Events:**
1. User opens the sounds list page.
2. System displays a list of sounds.
3. Each sound has the following information:
    - Title
    - Artist
    - Album (if applicable)
    - Play button
    - Like button (if logged in)
4. User can play a sound by clicking the play button.

**Alternative Flows:**
- No sounds match selected filters → System displays: "No sounds found."

**Postcondition:** User can view and listen to sounds.

---

### **UC4: Upload Sound (Creator)**

**Actor:** Creator
**Precondition:** Creator is logged in, and on the upload sound page.

**Flow of Events:**
1. Creator clicks "Upload Sound"
2. System displays upload form
3. Creator fills in the upload form including:
    - Title
    - Artist
    - Album (optional)
    - Sound File
4. Creator submits the upload form
5. System validates:
    - All required fields are filled
    - The sound file is a valid audio format
6. The system uploads the sound file.
7. The system creates a sound record in the database with the creator as the owner
8. System displays success message.

**Alternative Flows:**
- Invalid sound format → System displays an error message
- Creator does not fill in all the required fields → System displays an error message

**Postcondition:** Sound is uploaded and available for listening.

---

### **UC5: Create Playlist (Registered User)**

**Actor:** Registered User
**Precondition:** User is logged in. User is on their profile or playlist management page.

**Flow of Events:**
1. User clicks “Create Playlist”.
2. System displays a form for playlist creation:
    - Name
    - Description (optional)
3. User fills in the form and submits.
4. System validates:
    - The name is not empty.
5. System creates a new playlist in the database and associates it with the user.
6. System displays a success message.

**Alternative Flows:**
- User doesn't provide a name for the playlist → System displays an error message.

**Postcondition:** Playlist created and accessible to the user.

---

### **UC6: View Statistics (Admin)**

**Actor:** Admin
**Precondition:** Administrator is authorized and on the statistics dashboard.

**Flow of Events:**
1. Administrator selects period (day/week/month)
2. System retrieves data:
   - Total number of bookings
   - Revenue
   - Popular hotels
   - Room occupancy rates
3. Data is displayed as graphs and KPIs

**Postcondition:** Administrator receives complete statistics for the selected period.

---

### **UC7: Like Sound (Registered User)**

**Actor:** Registered User
**Precondition:** User is logged in and is on the sound details page.

**Flow of Events:**
1. User clicks on the like button.
2. System checks if the user has already liked the sound.
3. If the user has not liked the sound:
    - System adds a like to the sound and associates it with the user.
    - The like button changes to "Unlike".
4. If the user has already liked the sound:
   - System removes the like from the sound and the user.
   - The like button changes to "Like".

**Alternative Flows:**
- None

**Postcondition:** The sound is either liked or unliked by the user.

---

### **UC8: View Artist and Their Songs**

**Actor:** Guest / Registered User
**Precondition:** User is on the artist's page.

**Flow of Events:**
1. User navigates to artist's page.
2. System displays:
    - Artist's Name
    - Artist's photo (if available)
    - A list of songs by the artist.

**Alternative Flows:**
- No songs found for the artist → System displays "No songs found for this artist."

**Postcondition:** User can view the artist's information and listen to their songs.

---

### **UC9: View Playlist (Registered User/Guest)**

**Actor:** Registered User / Guest
**Precondition:** User is on the playlist page.

**Flow of Events:**
1. User opens the playlist page
2. System displays the list of sounds in the playlist.
3. For each sound:
    - Title
    - Artist
    - Album (if applicable)
    - Play Button
    - Like button(if logged in)

**Alternative Flows:**
- The playlist is empty → "Playlist is empty"

**Postcondition:** User can view the songs in the playlist and play the songs in the playlist.

---

### **UC10: Delete Sound (Creator)**

**Actor:** Creator
**Precondition:** The creator is logged in and owns the sound, and is on the sound details page or sound management page.

**Flow of Events:**
1. Creator clicks the “Delete” button.
2. System asks for confirmation: “Are you sure you want to delete this sound?”
3. Creator confirms the deletion
4. System deletes the sound from the database.
5. The sound file is removed from storage.
6. System displays a success message.

**Alternative Flows:**
- Creator cancels the deletion: Nothing happens.

**Postcondition:** The sound is deleted.

---

### **UC11: Edit Sound (Creator)**

**Actor:** Creator
**Precondition:** The creator is logged in and owns the sound, and is on the sound details page or sound management page.

**Flow of Events:**
1. Creator clicks the "Edit" button.
2. System displays an edit form with the following fields prepopulated with the sound's current information:
   - Title
   - Artist
   - Album (optional)
   - Sound File (optional)
3. The creator makes changes to the form and submits.
4. System Validates data.
5. System saves the sound changes.
6. System shows a success message.

**Alternative Flows:**
- The creator cancels the edit. Nothing happens.

**Postcondition:** Sound is updated with the new information.

---
