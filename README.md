
# Create firebase app boilerplate

Contains the directory structure and files that eases the creation of a firebase app.

### Directory layout

    .
    ├── functions                       # For cloud functions
    ├── src                             # Source files (alternatively `lib` or `app`)
    |    ├── assets                     # Stores any static file (Image/audio)
    │    ├── components                 # Any reusable code that can be used in the pages (Navbar, loading, etc.)
    |    ├── hooks                      # Custom code (function) that uses react hooks
    |         └── useFirebaseRef.js     # To listen/get value from the database
    |    |     
    |    ├── pages                      # Actual app’s pages
    |    ├── utils                      # Helper functions (FormatTime, ScoreCalculator, etc.)
    |    ├── App.js                     # Entry point to the application
    |    ├── config.js                  # Web app's Firebase configuration
    |    ├── context.js                 # Any global react context
    │    └── firebase.js                # Firebase initialization file  
    |    
    ├── .env                     
    ├── .gitignore                    
    ├── database.rules.json             # Database rules
    ├── firebase.json                   # Contains app's settings that will deployed
    ├── package.json            
    ├── rundev.js                       # To run the app in development environment
    └── README.md


## Usage/Examples

```javascript
npm run dev         # Executes the rundev.js file
npm run build       # Builds the project in production environment
```
### useFireBaseRef.js 
```javascript
const [value, loading] = useFirebaseRef( 
		path, once
	);
```
Returns:

- `value`: The `value` in the `path` specified, or `null` if `path` is wrong
- `loading`: A `boolean` to indicate whether the the `value` is still being loaded

#### Full Example
```js
const [properties, loading] = useFirebaseRef(
		'sessions/' + roomId + '/properties'
	);
    
	return (
		<div>
			{!loading ? <Discussion /> : <GameRounds /> : null}
		</div>
	);
```