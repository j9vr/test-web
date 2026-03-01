<script>
// Default owner account ALWAYS loads
let defaultUsers = [
    { username: "j9vr", password: "dxrp", isMember: true, isOwner: true }
];

// Load users OR apply defaults if none
let users = JSON.parse(localStorage.getItem("hiveUsers"));
if (!users || users.length === 0) {
    users = defaultUsers;
    localStorage.setItem("hiveUsers", JSON.stringify(users));
}

let currentUser = null;
let isOwner = false;

// Toggle login/register
let isRegister = false;
function toggleAuth() {
    isRegister = !isRegister;
    document.getElementById("authTitle").textContent = isRegister ? "Create Account" : "The Hive System Login";
    document.getElementById("authBtn").textContent = isRegister ? "Register" : "Login";
}

// Login or Register
function authenticate() {
    const username = document.getElementById("authUsername").value.trim();
    const password = document.getElementById("authPassword").value.trim();

    if (!username || !password) return alert("Enter username and password");

    // Register flow
    if (isRegister) {
        if (users.some(u => u.username === username)) return alert("Username already exists");

        users.push({ username, password, isMember: false, isOwner: false });
        localStorage.setItem("hiveUsers", JSON.stringify(users));
        alert("Account created. You can now log in.");
        toggleAuth();
        return;
    }

    // Login flow
    let user = users.find(u => u.username === username && u.password === password);
    if (!user) return alert("Wrong username or password");

    currentUser = user;
    isOwner = user.isOwner;

    document.getElementById("ownerPanelBtn").style.display = isOwner ? "block" : "none";

    document.getElementById("authScreen").style.display = "none";
    document.getElementById("hiveSystem").style.display = "block";

    refreshMembers();
}

// Logout
function logout() {
    currentUser = null;
    isOwner = false;
    document.getElementById("hiveSystem").style.display = "none";
    document.getElementById("authScreen").style.display = "flex";
}

// Toggle Owner Panel
function toggleOwnerPanel() {
    const panel = document.getElementById("ownerPanel");
    panel.style.display = panel.style.display === "block" ? "none" : "block";
}

// Refresh members list
function refreshMembers() {
    const display = document.getElementById("membersListDisplay");
    display.innerHTML = "";

    users.filter(u => u.isMember).forEach(u => {
        const div = document.createElement("div");
        div.className = "member";
        div.textContent = `${u.username}${u.isOwner ? " (Owner)" : ""}`;
        display.appendChild(div);
    });

    if (!isOwner) return;

    const ownerList = document.getElementById("membersList");
    ownerList.innerHTML = "";

    users.forEach((u, i) => {
        const div = document.createElement("div");
        div.className = "member";
        div.innerHTML = `
            ${u.username} ${u.isOwner ? "(Owner)" : "(Member)"}
            <div class="memberControl">
                <button class="delete" onclick="removeMember(${i})">Remove</button>
            </div>`;
        ownerList.appendChild(div);
    });

    localStorage.setItem("hiveUsers", JSON.stringify(users));
}

// Grant member
function grantMember() {
    const name = document.getElementById("grantUsername").value.trim();
    const u = users.find(x => x.username === name);
    if (!u) return alert("User not found");

    u.isMember = true;
    localStorage.setItem("hiveUsers", JSON.stringify(users));
    refreshMembers();
}

// Grant owner
function grantOwner() {
    const name = document.getElementById("grantUsername").value.trim();
    const u = users.find(x => x.username === name);
    if (!u) return alert("User not found");

    u.isOwner = true;
    localStorage.setItem("hiveUsers", JSON.stringify(users));
    refreshMembers();
}

// Remove member
function removeMember(i) {
    if (!confirm("Remove this user?")) return;
    users[i].isMember = false;
    users[i].isOwner = false;
    localStorage.setItem("hiveUsers", JSON.stringify(users));
    refreshMembers();
}
</script>
