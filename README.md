# API Documentation UserOccupation 

## /api/UserOccupation/{UserID}

### What It Does 
This API retrieves the details of the User Occupation based of the UserID 

### Inputs 
- {UserID}: The unique identifier for the user in the FashionWeather database

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

# API Documentation GetTemperature

## /api/GetTemperature/{WeatherID}

### What It Does 
This API retrives the temperature for the day bsaed on the WeatherID given 

### Inputs 
- {WeatherID}: The unique identifier for the Weather in the FashionWeather database

### Outputs
Returns the WeatherID, WeatherType, Temperature, and the Percipiation 
- int WeatherID
- string WeatherType
- string Temperature
- string Percipitation

### Sample Code 
```
        [HttpGet("{WeatherId}")]
        public async Task<ActionResult<List<Weather>>> GetTemperature(int WeatherId)
        {
            var temperatures = await _temperature.GetTemperature(WeatherId);
            if (temperatures == null)
            {
                return NotFound();
            }
            return temperatures;
        }
    }
```
