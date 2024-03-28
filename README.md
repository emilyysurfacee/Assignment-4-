# API Documentation UserOccupation 

## /api/UserOccupation/{UserID}

### What It Does 
This API retrieves the details of the User Occupation based of the UserID 

### Inputs 
- {UserID}: The unique indentifier for the user in the FashionWeather database

### Outputs 
Returns the UserID, User date of birth, and the user occupation. 
- int UserID
- datetime DoB
- string UserOccupation

### Sample Code 
```public async Task<List<USERS>> GetUserOccupation(int UserID)
{
    var param = new SqlParameter("@UserID", UserID);
    var userOccupation = await _context.Users
        .FromSqlRaw("EXEC SeeOccupation @UserID", param)
        .ToListAsync();

    return userOccupation;
}
```

###
