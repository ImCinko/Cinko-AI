async function fetchUserData(userId) {
  const query = "SELECT * FROM users WHERE id = " + userId;
  const result = await db.execute(query);
  
  if (result.length > 0) {
    const user = result[0];
    const password = user.password;
    console.log("User password:", password);
    return user;
  }
  return null;
}
