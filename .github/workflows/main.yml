None selected

Skip to content
Using Gmail with screen readers
1 of 5,189
(no subject)
Inbox

naseer lee <leenaseer@gmail.com>
Attachments
12:28 PM (9 minutes ago)
to me


 One attachment
  •  Scanned by Gmail
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Socially</title>
    <style>
        :root { 
            --bg-color: #f0f2f5; 
            --text-color: #1c1e21; 
            --card-bg: #ffffff; 
            --accent: #1877f2; 
            --accent-hover: #166fe5;
            --border-color: #e4e6eb;
            --secondary-text: #65676b;
            --danger-color: #e41e3f;
        }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: var(--bg-color); color: var(--text-color); margin:0; padding:0; }
        
        .screen { display: none; min-height: 100vh; align-items: center; justify-content: center; flex-direction: column; box-sizing: border-box; }
        .menu-card, .pfp-card { background: var(--card-bg); padding: 40px; border-radius: 16px; box-shadow: 0 4px 20px rgba(0,0,0,0.1); text-align: center; max-width: 420px; width: 90%; box-sizing: border-box; }
        
        .profile-circle { width: 160px; height: 160px; border-radius: 50%; border: 5px solid var(--accent); object-fit: cover; display: block; margin: 20px auto; }
        .pencil-icon { position: absolute; bottom: 10px; right: 10px; background: white; border-radius: 50%; width: 40px; height: 40px; display: flex; align-items: center; justify-content: center; font-size: 20px; cursor: pointer; box-shadow: 0 2px 8px rgba(0,0,0,0.2); }
        
        button { background: var(--accent); color: white; border: none; padding: 10px 14px; border-radius: 8px; cursor: pointer; font-size: 15px; font-weight: bold; transition: background 0.2s; }
        button:hover { background: var(--accent-hover); }
        input, textarea, select { width: 100%; padding: 12px; margin: 8px 0; border-radius: 8px; border: 1px solid #ccc; box-sizing: border-box; font-family: inherit; }
        
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); justify-content: center; align-items: center; z-index: 300; }
        .modal-content { background: var(--card-bg); padding: 25px; border-radius: 12px; width: 90%; max-width: 420px; max-height: 85vh; overflow-y: auto; }

        /* Navigation Layout */
        #feedScreen, #profileHubScreen { display: none; min-height: 100vh; flex-direction: column; align-items: center; background: var(--bg-color); padding-top: 75px; padding-bottom: 40px; }
        
        .navbar { position: fixed; top: 0; left: 0; right: 0; height: 60px; background: var(--card-bg); display: flex; align-items: center; justify-content: space-between; padding: 0 20px; box-shadow: 0 2px 4px rgba(0,0,0,0.08); z-index: 200; }
        .nav-profile { display: flex; align-items: center; gap: 10px; cursor: pointer; }
        .nav-avatar { width: 40px; height: 40px; border-radius: 50%; border: 2px solid var(--accent); object-fit: cover; }
        .nav-name { font-weight: bold; font-size: 16px; }
        .nav-right-controls { display: flex; align-items: center; gap: 10px; }
        
        /* Layout Grid for Feed + Right Sidebar */
        .app-layout { width: 100%; max-width: 900px; display: flex; gap: 20px; padding: 0 15px; box-sizing: border-box; align-items: flex-start; }
        .app-container { flex: 1; display: flex; flex-direction: column; gap: 20px; width: 100%; }
        
        /* Right Sidebar Search Area */
        .sidebar-right { width: 280px; position: sticky; top: 75px; display: flex; flex-direction: column; gap: 15px; }
        .search-card { background: var(--card-bg); border-radius: 12px; padding: 16px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); border: 1px solid var(--border-color); }
        .search-card h4 { margin: 0 0 10px 0; font-size: 16px; color: var(--text-color); }

        .create-post-card { background: var(--card-bg); border-radius: 12px; padding: 16px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        
        /* Post Structures */
        .post-card { background: var(--card-bg); border-radius: 12px; padding: 16px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); border: 1px solid var(--border-color); }
        .post-header { display: flex; align-items: center; gap: 10px; margin-bottom: 12px; }
        .post-avatar { width: 42px; height: 42px; border-radius: 50%; object-fit: cover; cursor: pointer; }
        .post-author { font-weight: bold; display: flex; align-items: center; gap: 4px; cursor: pointer; }
        .post-time { font-size: 12px; color: var(--secondary-text); }
        .post-title { font-size: 18px; font-weight: bold; margin: 5px 0; color: #000; }
        .post-text { font-size: 15px; line-height: 1.4; margin-bottom: 12px; white-space: pre-wrap; }
        .post-media { width: 100%; max-height: 400px; border-radius: 8px; object-fit: cover; margin-bottom: 12px; background: #000; }
        
        /* Action Elements */
        .post-actions { display: flex; gap: 15px; border-top: 1px solid var(--border-color); border-bottom: 1px solid var(--border-color); padding: 8px 0; margin-bottom: 10px; }
        .action-btn { background: none; color: var(--secondary-text); padding: 6px 12px; font-size: 14px; display: flex; align-items: center; gap: 6px; width: auto; margin: 0; }
        .action-btn:hover { background: #f2f3f5; color: var(--accent); }
        .action-btn.active { color: var(--accent); }

        /* Comments Engine */
        .comments-section { background: #f7f8fa; border-radius: 8px; padding: 10px; margin-top: 10px; display: none; }
        .comment-item { border-bottom: 1px solid #e4e6eb; padding: 6px 0; font-size: 14px; }
        .comment-item:last-child { border-bottom: none; }
        .comment-user { font-weight: bold; margin-right: 6px; cursor: pointer; }

        /* Profile Hub Layout */
        .profile-hub-header { background: var(--card-bg); border-radius: 12px; padding: 24px; text-align: center; border: 1px solid var(--border-color); position: relative; }
        .hub-stats { display: flex; justify-content: center; gap: 30px; margin: 15px 0; font-size: 16px; }
        .stat-num { font-weight: bold; color: var(--accent); display: block; font-size: 20px; }
        
        .hub-tabs { display: flex; border-bottom: 2px solid var(--border-color); margin-top: 20px; }
        .tab-btn { flex: 1; background: none; color: var(--secondary-text); border-radius: 0; padding: 12px; margin: 0; border-bottom: 3px solid transparent; }
        .tab-btn:hover { background: #e4e6eb; }
        .tab-btn.active { color: var(--accent); border-bottom-color: var(--accent); }
        
        .media-preview-container { max-height: 120px; overflow: hidden; border-radius: 8px; margin: 8px 0; display: none; }
        .media-preview-element { width: 100%; max-height: 120px; object-fit: cover; }

        .verified-badge { color: #1877f2; font-size: 14px; font-weight: bold; display: inline-flex; align-items: center; }
        .timer-warning { color: #d93025; font-weight: bold; margin-bottom: 10px; text-align: center; font-size: 14px; }

        /* Settings UI Items */
        .settings-section { border-bottom: 1px solid var(--border-color); padding: 12px 0; text-align: left; }
        .settings-section:last-child { border-bottom: none; }
        .settings-section h3 { margin: 0 0 10px 0; font-size: 16px; color: var(--accent); }
        .danger-btn { background: var(--danger-color); color: white; width: 100%; margin-top: 5px; }
        .danger-btn:hover { background: #c01833; }

        @media (max-width: 768px) {
            .app-layout { flex-direction: column-reverse; }
            .sidebar-right { width: 100%; position: static; }
        }
    </style>
</head>
<body>

    <!-- Welcome Menu -->
    <div id="menuScreen" class="screen" style="display:flex;">
        <div class="menu-card">
            <h1 style="color: var(--accent); font-size: 42px; margin: 0 0 10px 0;">Socially</h1>
            <p style="color:#555; margin-bottom: 30px;">Your session is safely saved on this browser device.</p>
            <button onclick="openSignInModal()" style="margin-bottom: 12px;">Sign In</button>
            <button onclick="openSignUpModal()" style="background:#42b72a;">Create New Account</button>
        </div>
    </div>

    <!-- Profile Picture Setup Screen -->
    <div id="pfpScreen" class="screen">
        <div class="pfp-card">
            <h2>Customize your Profile</h2>
            <p style="color:#666;">Set a picture to display on your dashboard layout</p>
            
            <div style="position:relative; display:inline-block;">
                <img id="setupProfilePic" class="profile-circle" src="https://via.placeholder.com/160">
                <div class="pencil-icon" onclick="document.getElementById('pfpFileInput').click()">✏️</div>
            </div>
            <input type="file" id="pfpFileInput" accept="image/*" style="display:none" onchange="setProfilePicture(event)">
            <button onclick="finishSetup()" style="margin-top: 20px;">Open Dashboard Feed →</button>
        </div>
    </div>

    <!-- Main Live Feed Screen Layout -->
    <div id="feedScreen">
        <div class="navbar">
            <div class="nav-profile" onclick="openProfileHub(currentUser.username)">
                <img id="navAvatar" class="nav-avatar" src="https://via.placeholder.com/160">
                <span id="navName" class="nav-name">Username</span>
            </div>
            <div class="nav-right-controls">
                <button onclick="openSettingsModal()" style="background:#e4e6eb; color:#050505; padding: 6px 12px; font-size: 14px;">⚙️ Settings</button>
                <button onclick="logout()" style="background:#666; padding: 6px 12px; font-size: 14px;">Logout</button>
            </div>
        </div>

        <div class="app-layout">
            <!-- Feed Left Main Container -->
            <div class="app-container">
                <!-- Create Post Card Dashboard -->
                <div class="create-post-card">
                    <h3 style="margin-top:0; margin-bottom:5px;">Create a Post</h3>
                    <input type="text" id="postTitleContent" placeholder="Enter a descriptive post title...">
                    <textarea id="postTextContent" placeholder="What is on your mind?" rows="3" style="resize:none; margin-top: 4px;"></textarea>
                    
                    <div class="media-preview-container" id="mediaPreviewBox"></div>

                    <div style="display: flex; gap: 10px; align-items: center; margin-top: 5px;">
                        <button onclick="document.getElementById('postFileInput').click()" style="background: #e4e6eb; color: #050505; flex: 1; font-size: 13px; padding: 8px;">📷 Add Image / Video</button>
                        <input type="file" id="postFileInput" accept="image/*,video/*" style="display:none;" onchange="handlePostMediaSelect(event)">
                        <button onclick="submitNewPost()" style="flex: 1; font-size: 13px; padding: 8px;">Publish Post</button>
                    </div>
                </div>

                <!-- Global Live Feed Container Box -->
                <div id="timelineFeedBox" style="display: flex; flex-direction: column; gap: 20px;"></div>
            </div>

            <!-- Right Sidebar Search Widget -->
            <div class="sidebar-right">
                <div class="search-card">
                    <h4>🔍 Search Feed</h4>
                    <input type="text" id="feedSearchInput" placeholder="Search titles or users..." oninput="handleSearchFilter()">
                </div>
            </div>
        </div>
    </div>

    <!-- Personal/User Profile Hub Dashboard Screen -->
    <div id="profileHubScreen">
        <div class="navbar">
            <div class="nav-profile" onclick="openGlobalFeed()">
                <span style="font-size: 20px; font-weight: bold; color: var(--accent);">← Back to Feed</span>
            </div>
            <div class="nav-right-controls">
                <button onclick="openSettingsModal()" style="background:#e4e6eb; color:#050505; padding: 6px 12px; font-size: 14px;">⚙️ Settings</button>
                <button onclick="logout()" style="background:#666; padding: 6px 12px; font-size: 14px;">Logout</button>
            </div>
        </div>

        <div class="app-container" style="max-width: 580px;">
            <div class="profile-hub-header">
                <img id="hubAvatar" class="profile-circle" style="width:110px; height:110px; margin:0 auto 10px auto;" src="https://via.placeholder.com/160">
                <h2 id="hubDisplayName" style="margin:0; display: flex; align-items: center; justify-content: center; gap: 6px;">Display Name</h2>
                <p id="hubUsername" style="margin:2px 0 15px 0; color: var(--secondary-text); font-size:14px;">@username</p>
                
                <button id="followSystemBtn" onclick="toggleFollowAction()" style="max-width: 160px; font-size: 14px; padding: 8px 16px; margin:0 auto; display:none;"></button>

                <div class="hub-stats">
                    <div><span id="followersCountText" class="stat-num">0</span>Followers</div>
                    <div><span id="followingCountText" class="stat-num">0</span>Following</div>
                </div>

                <!-- Structural Filter Activity Tabs -->
                <div class="hub-tabs">
                    <button id="tabPosts" class="tab-btn active" onclick="switchProfileTab('posts')">Posts</button>
                    <button id="tabLikes" class="tab-btn" onclick="switchProfileTab('likes')">Liked</button>
                    <button id="tabComments" class="tab-btn" onclick="switchProfileTab('comments')">Commented</button>
                </div>
            </div>

            <!-- Profile Categorized Output Stream target box -->
            <div id="profileHubStreamBox" style="display: flex; flex-direction: column; gap: 20px;"></div>
        </div>
    </div>

    <!-- Settings Modal -->
    <div class="modal" id="settingsModal">
        <div class="modal-content">
            <h2 style="margin-top:0;">⚙️ Account Settings</h2>

            <!-- Edit Username & Display Name Section -->
            <div class="settings-section">
                <h3>👤 Edit Account Details</h3>
                <label style="font-size: 12px; color: var(--secondary-text);">Username (Can only be changed once every 7 days)</label>
                <input type="text" id="settingsUsernameInput" placeholder="New Username">
                <div id="usernameLockMsg" style="font-size: 12px; color: #d93025; margin-bottom: 5px; display: none;"></div>

                <label style="font-size: 12px; color: var(--secondary-text);">Display Name</label>
                <input type="text" id="settingsDisplayNameInput" placeholder="New Display Name">

                <button onclick="saveAccountDetails()" style="width: 100%; margin-top: 5px;">Save Profile Changes</button>
            </div>

            <!-- Liked Content Privacy Option -->
            <div class="settings-section">
                <h3>🔒 Liked Posts / Videos Privacy</h3>
                <label style="font-size: 12px; color: var(--secondary-text);">Who can see posts you have liked?</label>
                <select id="likedPrivacySelect" onchange="savePrivacySettings()">
                    <option value="public">Public (Everyone)</option>
                    <option value="private">Private (Only Me)</option>
                </select>
            </div>

            <!-- Change PFP Section -->
            <div class="settings-section">
                <h3>🖼️ Change Profile Picture</h3>
                <div style="display: flex; align-items: center; gap: 15px;">
                    <img id="settingsPfpPreview" style="width: 60px; height: 60px; border-radius: 50%; object-fit: cover; border: 2px solid var(--accent);" src="https://via.placeholder.com/160">
                    <button onclick="document.getElementById('settingsPfpInput').click()" style="background: #e4e6eb; color: #050505;">Upload New Photo</button>
                    <input type="file" id="settingsPfpInput" accept="image/*" style="display:none;" onchange="updateSettingsPfp(event)">
                </div>
            </div>

            <!-- Danger Zone: Delete Account -->
            <div class="settings-section">
                <h3 style="color: var(--danger-color);">⚠️ Danger Zone</h3>
                <p style="font-size: 12px; color: var(--secondary-text); margin: 0 0 8px 0;">Deleting your account will erase everything including your posts, comments, and profile data.</p>
                <button class="danger-btn" onclick="deleteAccountPermanently()">Delete Account Permanently</button>
            </div>

            <button onclick="closeSettingsModal()" style="background:#666; margin-top: 15px; width:100%;">Close Settings</button>
        </div>
    </div>

    <!-- Popups Modals Infrastructure -->
    <div class="modal" id="signInModal">
        <div class="modal-content">
            <h2 style="margin-top: 0;">Sign In</h2>
            <input type="text" id="signinUser" placeholder="Username" onkeydown="if(event.key === 'Enter') executeSignIn()">
            <input type="password" id="signinPass" placeholder="Password" onkeydown="if(event.key === 'Enter') executeSignIn()">
            
            <button id="signinStartBtn" onclick="executeSignIn()">Verify Log In</button>
            
            <!-- 10-Second Confirmation Step Area -->
            <div id="loginConfirmArea" style="display: none; margin-top: 15px;">
                <div id="loginTimerText" class="timer-warning">Time remaining: 10s</div>
                <button id="confirmEntryBtn" onclick="confirmLoginAndProceed()" style="background: #42b72a; width: 100%;">Confirm & Enter Now →</button>
            </div>

            <button onclick="closeSignInModal()" style="background:#666; margin-top: 10px; width:100%;">Cancel</button>
        </div>
    </div>

    <div class="modal" id="signUpModal">
        <div class="modal-content">
            <h2 style="margin-top: 0;">Create Account</h2>
            <input type="text" id="signupUser" placeholder="Username" onkeydown="if(event.key === 'Enter') executeSignUp()">
            <input type="text" id="signupDisplay" placeholder="Display Name" onkeydown="if(event.key === 'Enter') executeSignUp()">
            <input type="password" id="signupPass" placeholder="Password" onkeydown="if(event.key === 'Enter') executeSignUp()">
            <button onclick="executeSignUp()">Create Account</button>
            <button onclick="closeSignUpModal()" style="background:#666; margin-top: 5px;">Cancel</button>
        </div>
    </div>

    <script>
        let dbInstance = null;
        let currentUser = null;
        let activeProfileUser = null; // Target profile user currently being viewed
        let pendingLoginUser = null;
        let loginTimerInterval = null;
        let attachedMediaData = null;
        let attachedMediaType = null;
        let activeHubTab = 'posts';

        // Banned Words List
        const BANNED_WORDS = [
            "fuck", "shit", "ass", "bitch", "cunt", "dick", "pussy", 
            "bastard", "slut", "whore", "damn", "crap", "asshole", "nigger", "faggot"
        ];

        function isBadUsername(input) {
            if (!input) return false;
            let cleaned = input.toLowerCase();
            const leetMap = { '0': 'o', '1': 'i', '!': 'i', '3': 'e', '4': 'a', '@': 'a', '5': 's', '$': 's', '7': 't', '8': 'b' };
            cleaned = cleaned.replace(/[01!34@5$78]/g, char => leetMap[char] || char);
            let ultraClean = cleaned.replace(/[^a-z0-9]/g, '');

            return BANNED_WORDS.some(badWord => ultraClean.includes(badWord) || cleaned.includes(badWord));
        }

        function escapeHTML(str) {
            if (!str) return '';
            return str.replace(/[&<>'"]/g, 
                tag => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', "'": '&#39;', '"': '&quot;' }[tag] || tag)
            );
        }

        function initStorageEngine() {
            return new Promise((resolve, reject) => {
                const request = indexedDB.open("SociallyDeepStoreDB", 3);
                request.onupgradeneeded = (e) => {
                    const database = e.target.result;
                    if (!database.objectStoreNames.contains("users")) {
                        database.createObjectStore("users", { keyPath: "username" });
                    }
                    if (!database.objectStoreNames.contains("posts")) {
                        database.createObjectStore("posts", { keyPath: "id", autoIncrement: true });
                    }
                };
                request.onsuccess = (e) => {
                    dbInstance = e.target.result;
                    resolve();
                };
                request.onerror = (e) => {
                    console.error("IndexedDB Error:", e);
                    reject(e);
                };
            });
        }

        function checkPersistentSession() {
            const savedUsername = localStorage.getItem("sociallyActiveUserSession");
            if (savedUsername) {
                const transaction = dbInstance.transaction(["users"], "readonly");
                transaction.objectStore("users").get(savedUsername).onsuccess = (e) => {
                    const userRecord = e.target.result;
                    if (userRecord) {
                        currentUser = userRecord;
                        openGlobalFeed();
                    } else {
                        localStorage.removeItem("sociallyActiveUserSession");
                    }
                };
            }
        }

        window.onload = async function() {
            await initStorageEngine();
            checkPersistentSession();
        };

        function openSignInModal() { 
            resetLoginTimerState();
            document.getElementById('signInModal').style.display = 'flex'; 
        }
        function closeSignInModal() { 
            resetLoginTimerState();
            document.getElementById('signInModal').style.display = 'none'; 
        }
        function openSignUpModal() { document.getElementById('signUpModal').style.display = 'flex'; }
        function closeSignUpModal() { document.getElementById('signUpModal').style.display = 'none'; }

        function executeSignUp() {
            const u = document.getElementById('signupUser').value.trim().toLowerCase();
            const d = document.getElementById('signupDisplay').value.trim() || u;
            const p = document.getElementById('signupPass').value;

            if (!u || !p) return alert("Username and Password are required!");

            if (isBadUsername(u) || isBadUsername(d)) {
                return alert("Account creation blocked! Your username or display name contains inappropriate language.");
            }

            const transaction = dbInstance.transaction(["users"], "readwrite");
            const store = transaction.objectStore("users");
            
            store.get(u).onsuccess = () => {
                if (store.get(u).result) {
                    return alert("This username is already taken. Please choose another one.");
                }

                const userObj = { 
                    username: u, 
                    display_name: d, 
                    password: p, 
                    profile_pic: "https://via.placeholder.com/160", 
                    social: { followers: 0, following: 0, followedByUser: false },
                    likedPrivacy: "public",
                    lastUsernameChange: null
                };
                
                store.put(userObj).onsuccess = () => {
                    currentUser = userObj;
                    localStorage.setItem("sociallyActiveUserSession", u);
                    closeSignUpModal();
                    showPfpScreen();
                };
            };
        }

        function executeSignIn() {
            const u = document.getElementById('signinUser').value.trim().toLowerCase();
            const p = document.getElementById('signinPass').value;

            if (!u || !p) return alert("Please fill in Username and Password.");

            const transaction = dbInstance.transaction(["users"], "readonly");
            const store = transaction.objectStore("users");
            store.get(u).onsuccess = (e) => {
                const userRecord = e.target.result;
                
                if (userRecord && userRecord.password === p) {
                    startLoginTimer(userRecord);
                } else {
                    alert("Authentication Failed: Account does not exist or password is wrong.");
                }
            };
        }

        function startLoginTimer(userRecord) {
            pendingLoginUser = userRecord;
            let timeLeft = 10;
            
            document.getElementById('signinStartBtn').style.display = 'none';
            document.getElementById('loginConfirmArea').style.display = 'block';
            document.getElementById('loginTimerText').innerText = `Time remaining: ${timeLeft}s`;

            clearInterval(loginTimerInterval);
            loginTimerInterval = setInterval(() => {
                timeLeft--;
                document.getElementById('loginTimerText').innerText = `Time remaining: ${timeLeft}s`;
                
                if (timeLeft <= 0) {
                    clearInterval(loginTimerInterval);
                    alert("Login expired! You did not press the confirm button in time (10s limit).");
                    resetLoginTimerState();
                }
            }, 1000);
        }

        function confirmLoginAndProceed() {
            if (!pendingLoginUser) return;
            
            clearInterval(loginTimerInterval);
            currentUser = pendingLoginUser;
            localStorage.setItem("sociallyActiveUserSession", currentUser.username);
            
            resetLoginTimerState();
            closeSignInModal();
            openGlobalFeed();
        }

        function resetLoginTimerState() {
            clearInterval(loginTimerInterval);
            pendingLoginUser = null;
            if(document.getElementById('signinStartBtn')) {
                document.getElementById('signinStartBtn').style.display = 'block';
            }
            if(document.getElementById('loginConfirmArea')) {
                document.getElementById('loginConfirmArea').style.display = 'none';
            }
        }

        function logout() {
            localStorage.removeItem("sociallyActiveUserSession");
            currentUser = null;
            document.getElementById('feedScreen').style.display = 'none';
            document.getElementById('profileHubScreen').style.display = 'none';
            document.getElementById('pfpScreen').style.display = 'none';
            document.getElementById('menuScreen').style.display = 'flex';
        }

        function showPfpScreen() {
            document.getElementById('menuScreen').style.display = 'none';
            document.getElementById('feedScreen').style.display = 'none';
            document.getElementById('profileHubScreen').style.display = 'none';
            document.getElementById('pfpScreen').style.display = 'flex';
            document.getElementById('setupProfilePic').src = currentUser.profile_pic || "https://via.placeholder.com/160";
        }

        function setProfilePicture(e) {
            const file = e.target.files[0];
            if (!file) return;

            if (file.size > 5 * 1024 * 1024) {
                alert("File size too large! Please choose an image under 5MB.");
                e.target.value = '';
                return;
            }

            const reader = new FileReader();
            reader.onload = ev => {
                const newPic = ev.target.result;
                document.getElementById('setupProfilePic').src = newPic;
                currentUser.profile_pic = newPic;
                
                const transaction = dbInstance.transaction(["users"], "readwrite");
                transaction.objectStore("users").put(currentUser);
                e.target.value = '';
            };
            reader.readAsDataURL(file);
        }

        function finishSetup() {
            openGlobalFeed();
        }

        /* Settings Functions */
        function openSettingsModal() {
            document.getElementById('settingsUsernameInput').value = currentUser.username;
            document.getElementById('settingsDisplayNameInput').value = currentUser.display_name;
            document.getElementById('likedPrivacySelect').value = currentUser.likedPrivacy || "public";
            document.getElementById('settingsPfpPreview').src = currentUser.profile_pic || "https://via.placeholder.com/160";
            
            const lockMsg = document.getElementById('usernameLockMsg');
            const ONE_WEEK_MS = 7 * 24 * 60 * 60 * 1000;
            if (currentUser.lastUsernameChange && (Date.now() - currentUser.lastUsernameChange < ONE_WEEK_MS)) {
                const daysRemaining = Math.ceil((ONE_WEEK_MS - (Date.now() - currentUser.lastUsernameChange)) / (1000 * 60 * 60 * 24));
                lockMsg.innerText = `🔒 Username locked for ${daysRemaining} more day(s).`;
                lockMsg.style.display = 'block';
                document.getElementById('settingsUsernameInput').disabled = true;
            } else {
                lockMsg.style.display = 'none';
                document.getElementById('settingsUsernameInput').disabled = false;
            }

            document.getElementById('settingsModal').style.display = 'flex';
        }

        function closeSettingsModal() {
            document.getElementById('settingsModal').style.display = 'none';
        }

        function savePrivacySettings() {
            const privacyVal = document.getElementById('likedPrivacySelect').value;
            currentUser.likedPrivacy = privacyVal;
            const tx = dbInstance.transaction(["users"], "readwrite");
            tx.objectStore("users").put(currentUser);
        }

        function saveAccountDetails() {
            const newUsername = document.getElementById('settingsUsernameInput').value.trim().toLowerCase();
            const newDisplay = document.getElementById('settingsDisplayNameInput').value.trim();

            if (!newUsername || !newDisplay) return alert("Username and Display Name cannot be empty!");
            
            if (isBadUsername(newUsername) || isBadUsername(newDisplay)) {
                return alert("Update blocked! Inappropriate language detected.");
            }

            const oldUsername = currentUser.username;
            const isUsernameChanging = newUsername !== oldUsername;

            if (isUsernameChanging) {
                const ONE_WEEK_MS = 7 * 24 * 60 * 60 * 1000;
                if (currentUser.lastUsernameChange && (Date.now() - currentUser.lastUsernameChange < ONE_WEEK_MS)) {
                    return alert("You can only change your username once every 7 days!");
                }

                const tx = dbInstance.transaction(["users"], "readwrite");
                const store = tx.objectStore("users");
                store.get(newUsername).onsuccess = (e) => {
                    if (e.target.result) {
                        return alert("Username already taken! Pick another.");
                    }

                    store.delete(oldUsername);
                    
                    currentUser.username = newUsername;
                    currentUser.display_name = newDisplay;
                    currentUser.lastUsernameChange = Date.now();

                    if (currentUser.social && currentUser.social.followers >= 1000000) {
                        currentUser.social.followers = 0; 
                    }

                    store.put(currentUser).onsuccess = () => {
                        localStorage.setItem("sociallyActiveUserSession", newUsername);
                        updateUserPostsOnUsernameChange(oldUsername, newUsername, newDisplay);
                        alert("Account details updated successfully!");
                        closeSettingsModal();
                        openGlobalFeed();
                    };
                };
            } else {
                currentUser.display_name = newDisplay;
                const tx = dbInstance.transaction(["users"], "readwrite");
                tx.objectStore("users").put(currentUser).onsuccess = () => {
                    alert("Display Name updated successfully!");
                    closeSettingsModal();
                    openGlobalFeed();
                };
            }
        }

        function updateUserPostsOnUsernameChange(oldU, newU, newDisplay) {
            const tx = dbInstance.transaction(["posts"], "readwrite");
            const store = tx.objectStore("posts");
            store.getAll().onsuccess = (e) => {
                const posts = e.target.result || [];
                posts.forEach(post => {
                    let dirty = false;
                    if (post.username === oldU) {
                        post.username = newU;
                        post.author = newDisplay;
                        dirty = true;
                    }
                    if (post.comments) {
                        post.comments.forEach(c => {
                            if (c.username === oldU) {
                                c.username = newU;
                                c.author = newDisplay;
                                dirty = true;
                            }
                        });
                    }
                    if (dirty) store.put(post);
                });
            };
        }

        function updateSettingsPfp(e) {
            const file = e.target.files[0];
            if (!file) return;

            if (file.size > 5 * 1024 * 1024) {
                alert("File size too large! Please choose an image under 5MB.");
                e.target.value = '';
                return;
            }

            const reader = new FileReader();
            reader.onload = ev => {
                const newPic = ev.target.result;
                document.getElementById('settingsPfpPreview').src = newPic;
                currentUser.profile_pic = newPic;
                
                const transaction = dbInstance.transaction(["users"], "readwrite");
                transaction.objectStore("users").put(currentUser).onsuccess = () => {
                    alert("Profile Picture Updated!");
                    openGlobalFeed();
                };
                e.target.value = '';
            };
            reader.readAsDataURL(file);
        }

        // Expanded Delete Account Function - deletes account, all created posts AND comments across other posts
        function deleteAccountPermanently() {
            if (!confirm("Are you SURE you want to delete your account? ALL posts and comments you have made will be permanently erased!")) {
                return;
            }

            const usernameToDelete = currentUser.username;

            const tx = dbInstance.transaction(["users", "posts"], "readwrite");
            tx.objectStore("users").delete(usernameToDelete);

            const postStore = tx.objectStore("posts");
            postStore.getAll().onsuccess = (e) => {
                const posts = e.target.result || [];
                posts.forEach(post => {
                    // Delete posts created by user
                    if (post.username === usernameToDelete) {
                        postStore.delete(post.id);
                    } else {
                        // Purge comments made by user on other posts
                        let modified = false;
                        if (post.comments) {
                            const originalLen = post.comments.length;
                            post.comments = post.comments.filter(c => c.username !== usernameToDelete);
                            if (post.comments.length !== originalLen) modified = true;
                        }
                        // Remove user's like if present
                        if (post.likedByUsers && post.likedByUsers.includes(usernameToDelete)) {
                            post.likedByUsers = post.likedByUsers.filter(u => u !== usernameToDelete);
                            post.likes = Math.max(0, post.likes - 1);
                            modified = true;
                        }
                        if (modified) {
                            postStore.put(post);
                        }
                    }
                });
            };

            tx.oncomplete = () => {
                alert("Account and all associated content permanently deleted!");
                closeSettingsModal();
                logout();
            };
        }

        function openGlobalFeed() {
            document.getElementById('menuScreen').style.display = 'none';
            document.getElementById('pfpScreen').style.display = 'none';
            document.getElementById('profileHubScreen').style.display = 'none';
            document.getElementById('feedScreen').style.display = 'flex';
            
            document.getElementById('navAvatar').src = currentUser.profile_pic || "https://via.placeholder.com/160";
            document.getElementById('navName').innerText = currentUser.display_name;
            renderTimelineFeed();
        }

        function openProfileHub(targetUsername) {
            const usernameToLoad = targetUsername || currentUser.username;
            
            const tx = dbInstance.transaction(["users"], "readonly");
            tx.objectStore("users").get(usernameToLoad).onsuccess = (e) => {
                activeProfileUser = e.target.result || currentUser;

                document.getElementById('feedScreen').style.display = 'none';
                document.getElementById('profileHubScreen').style.display = 'flex';
                
                document.getElementById('hubAvatar').src = activeProfileUser.profile_pic || "https://via.placeholder.com/160";
                
                let badgeMarkup = "";
                if (activeProfileUser.social && activeProfileUser.social.followers >= 1000000) {
                    badgeMarkup = `<span class="verified-badge" title="Verified Creator">🔹 Verified</span>`;
                }
                document.getElementById('hubDisplayName').innerHTML = `${escapeHTML(activeProfileUser.display_name)} ${badgeMarkup}`;
                document.getElementById('hubUsername').innerText = `@${activeProfileUser.username}`;
                
                if(!activeProfileUser.social) {
                    activeProfileUser.social = { followers: 0, following: 0, followedByUser: false };
                }
                
                renderFollowUI();
                switchProfileTab('posts');
            };
        }

        function renderFollowUI() {
            const btn = document.getElementById('followSystemBtn');
            const followersText = document.getElementById('followersCountText');
            const followingText = document.getElementById('followingCountText');

            followersText.innerText = activeProfileUser.social.followers;
            followingText.innerText = activeProfileUser.social.following;

            if (activeProfileUser.username !== currentUser.username) {
                btn.style.display = "block";
                btn.innerText = activeProfileUser.social.followedByUser ? "Unfollow" : "Follow";
                btn.style.background = activeProfileUser.social.followedByUser ? "#666" : "var(--accent)";
            } else {
                btn.style.display = "none";
            }
        }

        function toggleFollowAction() {
            if (activeProfileUser.username === currentUser.username) return;

            activeProfileUser.social.followedByUser = !activeProfileUser.social.followedByUser;
            activeProfileUser.social.followers += activeProfileUser.social.followedByUser ? 1 : -1;
            
            const transaction = dbInstance.transaction(["users"], "readwrite");
            transaction.objectStore("users").put(activeProfileUser);
            
            renderFollowUI();
        }

        function handlePostMediaSelect(e) {
            const file = e.target.files[0];
            if (!file) return;

            if (file.size > 5 * 1024 * 1024) {
                alert("File size too large! Please choose media under 5MB.");
                e.target.value = '';
                return;
            }
            
            attachedMediaType = file.type.startsWith('video/') ? 'video' : 'image';
            const reader = new FileReader();
            reader.onload = ev => {
                attachedMediaData = ev.target.result;
                const previewBox = document.getElementById('mediaPreviewBox');
                previewBox.style.display = 'block';
                previewBox.innerHTML = attachedMediaType === 'video' 
                    ? `<video src="${attachedMediaData}" class="media-preview-element" muted autoplay loop></video>`
                    : `<img src="${attachedMediaData}" class="media-preview-element">`;
                e.target.value = '';
            };
            reader.readAsDataURL(file);
        }

        function submitNewPost() {
            const titleContent = document.getElementById('postTitleContent').value.trim();
            const textContent = document.getElementById('postTextContent').value.trim();
            
            if (!titleContent) return alert("Every post requires a Title entry!");
            if (!textContent && !attachedMediaData) return alert("Cannot publish an empty post!");

            if (isBadUsername(titleContent) || isBadUsername(textContent)) {
                return alert("Post blocked! Your title or content contains inappropriate language.");
            }

            const postObj = {
                username: currentUser.username,
                author: currentUser.display_name,
                avatar: currentUser.profile_pic,
                title: titleContent,
                text: textContent,
                media: attachedMediaData,
                mediaType: attachedMediaType,
                timestamp: new Date().toLocaleString(),
                createdTime: Date.now(),
                likes: 0,
                likedByUsers: [],
                comments: [],
                followersCountAtPost: currentUser.social ? currentUser.social.followers : 0 
            };

            const transaction = dbInstance.transaction(["posts"], "readwrite");
            transaction.objectStore("posts").add(postObj).onsuccess = () => {
                document.getElementById('postTitleContent').value = "";
                document.getElementById('postTextContent').value = "";
                document.getElementById('mediaPreviewBox').style.display = 'none';
                attachedMediaData = null;
                attachedMediaType = null;
                renderTimelineFeed();
            };
        }

        function handleSearchFilter() {
            renderTimelineFeed();
        }

        // Timeline feed sorts by standard popularity (More likes = higher up in feed)
        function renderTimelineFeed() {
            const timelineBox = document.getElementById('timelineFeedBox');
            const filterText = (document.getElementById('feedSearchInput')?.value || "").trim().toLowerCase();
            timelineBox.innerHTML = "";

            const transaction = dbInstance.transaction(["posts"], "readonly");
            transaction.objectStore("posts").getAll().onsuccess = (e) => {
                let posts = e.target.result || [];
                let visibleCount = 0;

                // Sort algorithm: Most likes top, tiebreaker by newest creation timestamp
                posts.sort((a, b) => {
                    const likesA = a.likes || 0;
                    const likesB = b.likes || 0;
                    if (likesB !== likesA) {
                        return likesB - likesA;
                    }
                    return (b.createdTime || 0) - (a.createdTime || 0);
                });

                posts.forEach(post => {
                    const matchTitle = post.title && post.title.toLowerCase().includes(filterText);
                    const matchAuthor = (post.author && post.author.toLowerCase().includes(filterText)) || 
                                        (post.username && post.username.toLowerCase().includes(filterText));

                    if (!filterText || matchTitle || matchAuthor) {
                        timelineBox.appendChild(buildPostHTMLNode(post));
                        visibleCount++;
                    }
                });

                if(visibleCount === 0) {
                    timelineBox.innerHTML = `<p style="text-align:center; color:#666; padding: 20px;">No updates match your search.</p>`;
                }
            };
        }

        function buildPostHTMLNode(post) {
            const card = document.createElement('div');
            card.className = "post-card";
            
            let mediaMarkup = "";
            if (post.media) {
                mediaMarkup = post.mediaType === 'video' 
                    ? `<video src="${post.media}" class="post-media" controls></video>`
                    : `<img src="${post.media}" class="post-media">`;
            }

            const clientLiked = post.likedByUsers && post.likedByUsers.includes(currentUser.username);

            let authorBadgeMarkup = "";
            if (post.followersCountAtPost && post.followersCountAtPost >= 1000000) {
                authorBadgeMarkup = `<span class="verified-badge" title="Verified Creator" style="font-size:12px;">🔹 Verified</span>`;
            }

            card.innerHTML = `
                <div class="post-header">
                    <img class="post-avatar" src="${post.avatar || 'https://via.placeholder.com/160'}" onclick="openProfileHub('${escapeHTML(post.username)}')">
                    <div>
                        <div class="post-author" onclick="openProfileHub('${escapeHTML(post.username)}')">${escapeHTML(post.author)} (@${escapeHTML(post.username)}) ${authorBadgeMarkup}</div>
                        <div class="post-time">${escapeHTML(post.timestamp)}</div>
                    </div>
                </div>
                <div class="post-title">${escapeHTML(post.title)}</div>
                ${post.text ? `<div class="post-text">${escapeHTML(post.text)}</div>` : ''}
                ${mediaMarkup}
                
                <div class="post-actions">
                    <button class="action-btn ${clientLiked ? 'active' : ''}" onclick="toggleLike(${post.id}, this)">
                        👍 Like (<span id="likeCount-${post.id}">${post.likes || 0}</span>)
                    </button>
                    <button class="action-btn" onclick="toggleCommentsView(${post.id})">
                        💬 Comments (<span id="commentCount-${post.id}">${post.comments ? post.comments.length : 0}</span>)
                    </button>
                </div>

                <div class="comments-section" id="commentsBox-${post.id}">
                    <div id="commentsList-${post.id}" style="margin-bottom: 8px; max-height: 200px; overflow-y:auto;"></div>
                    <div style="display:flex; gap: 8px;">
                        <input type="text" id="commentInput-${post.id}" placeholder="Write a comment..." style="margin:0; padding:8px;" onkeydown="if(event.key === 'Enter') submitComment(${post.id})">
                        <button onclick="submitComment(${post.id})" style="padding: 4px 12px; font-size:13px; width:auto;">Post</button>
                    </div>
                </div>
            `;
            
            const listTarget = card.querySelector(`#commentsList-${post.id}`);
            if(post.comments && post.comments.length > 0) {
                post.comments.forEach(c => {
                    const el = document.createElement('div');
                    el.className = "comment-item";
                    el.innerHTML = `<span class="comment-user" onclick="openProfileHub('${escapeHTML(c.username)}')">${escapeHTML(c.author)}:</span><span>${escapeHTML(c.text)}</span>`;
                    listTarget.appendChild(el);
                });
            } else {
                listTarget.innerHTML = `<p style="font-size:12px; color:#666; margin:4px 0;">No responses added.</p>`;
            }

            return card;
        }

        function toggleLike(postId, btnElement) {
            const transaction = dbInstance.transaction(["posts"], "readwrite");
            const store = transaction.objectStore("posts");
            store.get(postId).onsuccess = (e) => {
                const post = e.target.result;
                if(!post) return;
                if(!post.likedByUsers) post.likedByUsers = [];
                
                const idx = post.likedByUsers.indexOf(currentUser.username);
                if(idx > -1) {
                    post.likedByUsers.splice(idx, 1);
                    post.likes = Math.max(0, post.likes - 1);
                } else {
                    post.likedByUsers.push(currentUser.username);
                    post.likes = (post.likes || 0) + 1;
                }
                
                store.put(post).onsuccess = () => {
                    const counter = document.getElementById(`likeCount-${postId}`);
                    if(counter) counter.innerText = post.likes;
                    
                    if(btnElement) btnElement.classList.toggle('active');
                    if(document.getElementById('profileHubScreen').style.display === 'flex') {
                        switchProfileTab(activeHubTab);
                    } else {
                        renderTimelineFeed(); // Re-sort feed dynamically when likes change
                    }
                };
            };
        }

        function toggleCommentsView(postId) {
            const box = document.getElementById(`commentsBox-${postId}`);
            box.style.display = box.style.display === 'block' ? 'none' : 'block';
        }

        function submitComment(postId) {
            const inputField = document.getElementById(`commentInput-${postId}`);
            const text = inputField.value.trim();
            if(!text) return;

            if (isBadUsername(text)) {
                return alert("Comment blocked! Your message contains inappropriate language.");
            }

            const transaction = dbInstance.transaction(["posts"], "readwrite");
            const store = transaction.objectStore("posts");
            store.get(postId).onsuccess = (e) => {
                const post = e.target.result;
                if(!post) return;
                if(!post.comments) post.comments = [];
                
                post.comments.push({
                    username: currentUser.username,
                    author: currentUser.display_name,
                    text: text
                });

                store.put(post).onsuccess = () => {
                    inputField.value = "";
                    const countEl = document.getElementById(`commentCount-${postId}`);
                    if(countEl) countEl.innerText = post.comments.length;
                    
                    const listTarget = document.getElementById(`commentsList-${postId}`);
                    if(post.comments.length === 1) listTarget.innerHTML = "";
                    
                    const el = document.createElement('div');
                    el.className = "comment-item";
                    el.innerHTML = `<span class="comment-user" onclick="openProfileHub('${escapeHTML(currentUser.username)}')">${escapeHTML(currentUser.display_name)}:</span><span>${escapeHTML(text)}</span>`;
                    listTarget.appendChild(el);
                };
            };
        }

        function switchProfileTab(tabName) {
            activeHubTab = tabName;
            document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
            if(tabName === 'posts') document.getElementById('tabPosts').classList.add('active');
            if(tabName === 'likes') document.getElementById('tabLikes').classList.add('active');
            if(tabName === 'comments') document.getElementById('tabComments').classList.add('active');

            const outputContainer = document.getElementById('profileHubStreamBox');
            outputContainer.innerHTML = "";

            // Check Privacy Rules for Liked Content Tab
            if (tabName === 'likes' && activeProfileUser.username !== currentUser.username && activeProfileUser.likedPrivacy === "private") {
                outputContainer.innerHTML = `<p style="text-align:center; color:#666; padding: 20px;">🔒 This user has set their liked posts/videos to private.</p>`;
                return;
            }

            const transaction = dbInstance.transaction(["posts"], "readonly");
            transaction.objectStore("posts").getAll().onsuccess = (e) => {
                const posts = e.target.result || [];
                let matchCounter = 0;

                posts.reverse().forEach(post => {
                    let shouldRender = false;
                    
                    if(tabName === 'posts' && post.username === activeProfileUser.username) shouldRender = true;
                    if(tabName === 'likes' && post.likedByUsers && post.likedByUsers.includes(activeProfileUser.username)) shouldRender = true;
                    if(tabName === 'comments' && post.comments && post.comments.some(c => c.username === activeProfileUser.username)) shouldRender = true;

                    if(shouldRender) {
                        matchCounter++;
                        outputContainer.appendChild(buildPostHTMLNode(post));
                    }
                });

                if(matchCounter === 0) {
                    outputContainer.innerHTML = `<p style="text-align:center; color:#666; padding: 20px;">No matching activity found.</p>`;
                }
            };
        }
    </script>
</body>
</html>
index.html
Displaying index.html.
