 
Create Next App 

Section 1-Create Next App 

1.NPX Create react app 

 

 
2.Next-Amazona 
3.Add ES.LINT 
4. Add all dependencies needed as well 
5.NPM Run dev 

6.Install NPM Material UI 
Ran into an error here but I fixed it with a fix-the-upstream-dependency 
https://stackoverflow.com/questions/64936044/fix-the-upstream-dependency-conflict-installing-npm-packages 
 

7.Delete everything from the Index.js 
<Layout> 

<h1> 
<ul> 
	<li>   </li> 
	<li>   </li> 
	<li>   </li> 
</ul> 
</h1> 
</Layout> 
 

8. Components and add a layout file  
Ran into an error with React 
https://stackoverflow.com/questions/68163385/parsing-error-cannot-find-module-next-babel 

9. RFC and create a file and import a header and import amazona 
10. <title>Next Amazona</title> 

11.App bar”Position” -Static 

12.Import App bar and tool bar 
13.Toolbar and typography 
14.Add Container and add children Container {Children} 
15.Import children  

16. Add footer and add ALL RIGHTS RESERVED to the footer.  
 
Add styles to app 
1.Add styles to our amazona project 
2.Similar to css use a style called make styles from material ui 
3.Create a utils and add styles.js 
4.Add const useStyles = makeStyles and add import {makeStyles} from “@material-ui/core” 
5.const useStyles = makeStyles({ 
	navbar:{ 
		backgroundColor: ‘#203040’ //use hashtag for color and camalcase 
		‘& a’:{ 
			color: ‘#ffffff’, 
		              marginLeft: 10, 
			   
		}, 
	}, 
}); 
6. Export default useStyle 
7.Go to layout and import useStyles from ‘../utils/styles’; 
8.Import const classes = useStyles(); 
9.Go to AppBar and set a classname = {classes.navbar} and the color changes 
10.Go to styles and add main and add minHeight’80vh’ 
11. And add className={classes.main} and adds a space 
12.Go to styles for footer and set textAlign: ‘center 
13. Go to footer and classname and set it = classes.footer 
 
Fixing the material UI SSR issue 
1. Go to useEffect(()=> { 
		const jssStyles = document.querySelector(‘#jss-server-site’) 
},[]); 
2. If this condition exists{ 
just remove it. 
3. useEffect(() => { 

const jssStyles = document.querySelector('#jss-server-side'); 

if (jssStyles) { 

jssStyles.parentElement.removeChild(jssStyles); 

} 

}, []); 

 
4. Make an _document.js in the pages file, this changes the way our pages render using next.js 
5. Export default class MyDocument extends Document {} 
6. Have to import document from ‘next/document’ 
7. Return ( <html> which imports to ‘next/document’ 
8. render() { 

return ( 

<Html lang="en"> 

<Head></Head> 

<body> 

<Main /> 

<NextScript /> 

</body> 

</Html> 

); 

} 

} 

9.Inside the body section going to render the main and nextscript 
10.Next step is going to be initializing get initial props 
11. MyDocument.getInitialProps = async (ctx) => { 

const sheets = new ServerStyleSheets(); 

const originalRenderPage = ctx.renderPage; 

ctx.renderPage = () => { 

return originalRenderPage({ 

enhanceApp: (App) => (props) => sheets.collect(<App {...props} />), 

}); 

}; 

const initialProps = await Document.getInitialProps(ctx); 

return { 

...initialProps, 

styles: [ 

...React.Children.toArray(initialProps.styles), 

sheets.getStyleElement(), 

], 

}; 

}; 
12.Import serverstylesshets which comes from materialui core 

13.Get originalrenderpage from ctx render.page and change render page function 
14.ctx.renderpage = call original is an object with enhanceapp accepts app as a parameter, which returns props as another function and add sheets.collect and return the app with props as a parameter 

15.Const initialProps = await document.getinitialprops(ctx) 

16.All elements need to be returned in initial props and have to add styles 

17.Add react children.toArray and add initialprops and sheets.get style element(); 
 
List Products 
1.Data.js add the file to your project and create an input where you can download all your files 
2. products: [ 

{ 

name: 'Free Shirt', 

category: 'Shirts', 

image: '/images/shirt1.jpg', 

price: 70, 

brand: 'Nike', 

rating: 4.5, 

numReviews: 10, 

countInStock: 20, 

description: 'A popular shirt.', 

}, 

 
3. Add like 5 products with all the categories using an object to store the values 
4.Then go to the source code and get all the images that are necessary to download the files 
5.Then go to your index.js and import Grid with a container of 3 with data.products.map((product) => 
<Grid item md={4} key={product.name} </Grid> 
6.Get rid of styles and add data from import data from ‘utils/data’ 
7.Then import card and import Card action and add card media with component =”img” 
with an image and with a title and import CartItem as well 
8.Then import typography as well with product.name 
9. Add the cart actions and add typography and add product.price with typography and make sure all the things are imported  
10.Define a button and import add to cart and set the button size to small and the color primary 
11.What the source code looks like 
<Layout> 

<div> 

<h1>Products</h1> 

<Grid container spacing={3}> 

{data.products.map((product) => ( 

<Grid item md={4} key={product.name}> 

<Card> 

<CardActionArea> 

<CardMedia 

component="img" 

image={product.image} 

title={product.name} 

></CardMedia> 

<CardContent> 

<Typography>{product.name}</Typography> 

</CardContent> 

</CardActionArea> 

<CardActions> 

<Typography>${product.price}</Typography> 

<Button size="small" color="primary"> 

Add to cart 

</Button> 

</CardActions> 

</Card> 

</Grid> 

))} 

</Grid> 

</div> 

</Layout> 

 
 
Add Header Links 
1.Import NextLink from nextjs(Ignore this though because wrapping it around Link for some reason causes an error and I don’t know why hes wrapping nextlink and link, as this is causing a hydration error. (This might become an issue later but at the moment it isn’t) 

 
2.if you add it then it will be converted as href 

 
3.Go to classname and add brand and then from there add brand styling  
<Typography className={classes.brand}>amazona</Typography> 
 
4.Go to classname and add brand and then from there add brand styling  
navbar: { 

backgroundColor: '#203040', 

'& a': { 

color: '#ffffff', 

marginLeft: 10, 

}, 

}, 

brand: { 

fontweight: 'bold', 

fontSize: '1.5rem', 

}, 

 

5.Add a flexgrow to 1 and then add link href of cart and login, again the issue is nextlink and wrapping link maybe its my server or something. 

 

Route Product Page 
 
1.Nextlink and wrap the card action area 
2.set href to product slug and pass href <NextLink href={`/product/${product.slug}`} passHref> 
3.Nextlink and wrap the card action area 
4. Go to data.js in the utils folder and for each product set the slug 
5. Free-shirt 
6. Create a product folder and then from there create [slug] for dynamic routing 
7.Import React and import router and change slug to product screen 
8. Const router = useRouter(); 
9. Const {slug}= data.products.find(a=> a.slug===slug); 
10.If(!product){ 
return <div>Product Not Found</div> 
11. Return <div> <h1>{product.name}</h1></div> 
 
Build Product Page 
1.Open slug in product folder and add <Layout> form components folder 
 
2. Import Layout from components 
 
3.<Layout title={product.name}> 
 
4. <Layout title={product.name}> 
 
5.NextLink from ‘next/link’ 
 
6. Head and use it in the title section of <Head><title>Next Amazona</title> 
 
7. Create curly brackets {title ? `${title}-Next Amazona` : ‘Next Amazona’} title 
 
8. Add href = passhref=”” 
 
9.Div className={classes.section}> 
 
10. Const classes = useStyles from utils.styles 
 
11.Go to styles.js and go to section and for section for marginTop:10px, marginBottom:10px 
 
12. Grid container spacing={1}> and import grid 
 
13. Inside the grid define another grid and grid item md=6 
 
14. Add Image src={product. Image} set alternative text set with to width={64} 
 
15. Set layout to responsive  
 
16. Import Image from ‘next/image’ 
 
17.Import grid item md={3} xs={12}> <List></List></Grid>  
<ListItem>  
 
18. Set Category={product. Category} and add Category brand and Category Rating 
 
19.<ListItem>Description: </ListItem> 
 
20.Import typography from material ui<Grid> 
 
21.Wrap all items in typography 
 
22.Add a grid item={md} xs={12} and add <Card></Card> 
 
23.And we’re going to create a border around it 
 
24.Import card and then import <List> and a <ListItem></Listitem> and add <Grid container> and add <Grid item> and add price product.price 
 
25.Set item xs={6} and then create another one grid item xs={6} 
 
26.Add countinstock>0 available and unavailable 
 
27.Add a button and then add another button 
 
28.Add styling fullwidth variant color to add to cart 
 
29.Go to footer and add margintop:10 
 
30.Add description and meta tag to title and add a h1 tag 
 
Add Material Ui to our project 

1.Add const theme = createMuiTheme 

2.Add createMuiTheme into material-ui/core 

3.Typography:{ h1:{ fontSize:'1.6rem', fontWeight:400, margin: '1rem 0' } h2:{ fontSize:'1.4rem', fontWeight:400, margin: '1rem 0' }, } 

Add ThemeProvider theme={theme} 

5. 

6.Add a slug and add a variant 

Add Head and add Head 

8.palette: { type: 'light', primary: { main: '#f0c000', }, secondary: { main: '#208080', }, }, 
 
Import switch design 

1.Import { createContext,useReducer} from "react" 

  

2.export const store =  {createContext} 

  

3.const InitialState ={ 

darkMode: false 

} 

  

4.Export function StoreProvider(props){ 

const[state,dispatch] = useReducer(reducer,initialstate) 

  

5.Add eslint reccomended 

  

6.  const [state, dispatch] = useReducer(reducer, initialState); 

  

7.function reducer(state, action) {  

  switch (action.type) { 

    case 'DARK_MODE_ON': 

      return { ...state, darkMode: true }; 

    case 'DARK_MODE_OFF': 

      return { ...state, darkMode: false }; 

    default: 

      return state; 

  } 

} 

  

8.Layout const {state,dispatch} = useContext() 

  

9.Import {store} from '../utils/store' 

  

10. type: darkMode ? 'dark' : 'light', 

  

11.Set the darkmode to true. 

  

12. Add a Layoutjs Switch checked={darkmode} onChange={darkmodechallenger} 

  

13.Const darkmodechangehandler dispatch type darkmode  dispatch({ type: darkMode ? 'DARK_MODE_OFF' : 'DARK_MODE_ON' }); 

  

14.Install NPM install cookie 

  

15. Const newDarkMode= !darkmode 

  

16.Cookies.set('darkMode', newDarkMode ? 'ON' : 'OFF'); 

  

17.darkMode: Cookies.get('darkMode') === 'ON' ? true : false, 
 
 
Connect Mongodb 

1.NPM install mongoose 

  

2.Import const connection={} 

  

3.Add async function() { 

if(connection.isConnected){ 

console.log('already connected') 

return; 

} 

  

4.Env, browser = true, node=true 

  

5.if(connection.isConnected){ 

console.log('already connected') 

return; 

} 

  

6.if(mongoose.connections.length>0){ 

connection.isConnected= mongoose.connections[0].readyState 

if(connected.isConnected===1){ 

console.log(use previous connection) 

return  

} 

  

7. Await mongoose.disconnect 

  

8.const db = await mongoose.connect(process.env.MONGODB_URI); //this sets the connection 

  console.log('new connection'); 

  connection.isConnected = db.connections[0].readyState; 

} 

  

9.async function disconnect() { 

  if (connection.isConnected) { 

    if (process.env.NODE_ENV === 'production') { 

      await mongoose.disconnect(); 

      connection.isConnected = false; 

    } else { 

      console.log('not disconnected'); 

    } 

  } 

} 

  

  

10. Add env file and connect it to mongodb. Check the env file with the hello 
 
Building out Product API 

  

1.Product.js has a mongoose and adds mongoose then from there we add all the categories that are necessary 

  

import mongoose from 'mongoose'; 

  

const productSchema = new mongoose.Schema( 

  { 

    name: { type: String, required: true }, 

    slug: { type: String, required: true, unique: true }, 

    category: { type: String, required: true }, 

    image: { type: String, required: true }, 

    price: { type: Number, required: true }, 

    brand: { type: String, required: true }, 

    rating: { type: Number, required: true, default: 0 }, 

    numReviews: { type: Number, required: true, default: 0 }, 

    countInStock: { type: Number, required: true, default: 0 }, 

    description: { type: String, required: true }, 

  }, 

  { 

    timestamps: true, 

  } 

); 

  

2. 

const Product = 

  mongoose.models.Product || mongoose.model('Product', productSchema); 

export default Product; 

  

3.Creates a new sentence letter and from there you can add mongoose.models.product or the mongoose.model 

  

4.Download next-connect 

  

5.Create a handler =nc(), while importing db from '../utils/db' 

  

6 Import import nc from 'next-connect'; 

import Product from '../../../models/Product'; 

import db from '../../../utils/db'; 

  

const handler = nc(); 

  

handler.get(async (req, res) => { 

  await db.connect();   

  const products = await Product.find({}); 

  await db.disconnect(); 

  res.send(products); 

}); 

  

export default handler; 

  

//this is used to connect the database 

  

7.Copy the whole index.js and import it to the seed part 

  

8. When I get to the seed from there make changes to the seed 

  

9.import nc from 'next-connect'; 

import Product from '../../models/Product'; 

import db from '../../utils/db'; 

import data from '../../utils/data'; 

  

const handler = nc(); 

  

handler.get(async (req, res) => { 

  await db.connect(); 

  await Product.deleteMany(); 

  await Product.insertMany(data.products); 

  await db.disconnect(); 

  res.send({ message: 'seeded successfully' }); 

}); 

  

export default handler; 

  

10.Big thing is to make sure the mongodb database is succesfully connected and readandwrite is used in your username. Other than that self explanatory section as we're using nextjs syntax to connect a database 

  

  

 Getting data from the mongodb instead 

1.export async function getServerSideProps() { 

  await db.connect(); 

  const products = await Product.find({}).lean(); 

  await db.disconnect(); 

  return { 

    props: { 

      products: products.map(db.convertDocToObj), 

    }, 

  }; 

} 

  

use getserversideprops 

  

2.Import product from '../models/product' 

  

3.Props and const {products} = prop 

  

4.get the props from the  {products.map((product) => ( 

            <Grid item md={4} key={product.name}> 

  

rather than before from data.map 

  

5.Import lean then import function convert to doc  

  

6.function convertDocToObj(doc) { 

  doc._id = doc._id.toString(); 

  doc.createdAt = doc.createdAt.toString(); 

  doc.updatedAt = doc.updatedAt.toString(); 

  return doc; 

} 

  

7.go to slug converts it to js 

  

export async function getServerSideProps() { 

  await db.connect(); 

  const products = await Product.find({}).lean(); 

  await db.disconnect(); 

  return { 

    props: { 

      products: products.map(db.convertDocToObj), 

    }, 

  }; 

} 

  

8. add params= context 
 

9.And import slug{} 
 

10.findone{slug} 

  

11.const product{slug} 

  

12.convert change product: db.covert to obj(product) 
 
Installing the authentication 

1.NPM I next-auth 
2.Create a file [...nextauth] and import next[auth] 
3.Import export default nextAuth({ 
	session:{ 
	strategy: ‘jwt’, // 
}, 
callbacks:{ 
	        async jwt({ token, user}){ 
		if(user?._id) token._id = user._id; 
              if(user?.isAdmin) token.isAdmin = user.isAdmin; 
	return token; 
          } 
async session({ session, token}){ 
      if(token?._id) session.user._id = token._id; 
      if(token?.isAdmin) session.user.isAdmin = token.isAdmin; 
      return session; 
  } , 
}, 
providers: [ 
	CredentialsProvider({ 
			async authorize(credentials){ 
				await db.connect(); 
			         const user = await User.findOne({ 
				email:credentials.email, 
			}); 
			await db.disconnect(); 
			if(user && bcryptjs.compareSync(credentials.password,user.password)){ 
			return { 
			_id: user._id, 
			         name: user.name, 
			email:user.email, 
			   image: ‘f’, 
			      isAdmin: user.isAdmin, 
}; 
} 
throw new Error(‘Invalid email or password’) 
} 
}) 
 
providers:{ 
} 
} 
 
4. Go to the submit handler in login js and get the try and catch error const result = await signIn(‘credential) 
rediect:false, 
email, 
password, 
}); 
catch(err){ 
} 
 
5.Catch(err){ 
toast.error(getError(err)); 
} 
 
6.Add utils and add error.js 
 
const getError = (err) => 

err.response && err.response.data && err.response.data.message 

? err.response.data.message 

: err.message; 

 
 

export { getError }; 
 
7. Go to login JS add toast error and install npm I react-toastify 
 
8.Import {toast container}  and install {toast} 
 
9.Const {data : session} = useSession(); 
 
10. useEffect(() => { 

if (session?.user) { 

router.push(redirect || '/'); 

} 

}, [router, session, redirect]); 
 
11. Have to import use session from next-auth/react 
 
12.Then go to app.js and then go to session provider session={session} 
 
13. function MyApp({ Component, pageProps: { session, ...pageProps } }) { 
 
14. Import session  
const { status, data: session } = useSession(); 
 
15.Show user name and show the login and import react-toastify/React toastify 
 
 
Add User Menu to navbar 
1.NPM install @headless ui 
 
2.Import Menu to the navbar as well /layout page as the navbar is there 
 
3. <Menu.Button className="text-blue-600"> 

{session.user.name} 

</Menu.Button> 

<Menu.Items className="absolute right-0 w-56 origin-top-right bg-white shadow-lg"> 

<Menu.Item> 

<DropdownLink className="dropdown-link" href="/profile"> 

Profile 

</DropdownLink> 

</Menu.Item> 

<Menu.Item> 

<DropdownLink 

className="dropdown-link" 

href="/order-history" 

> 

Order History 

</DropdownLink> 

</Menu.Item> 

<Menu.Item> 

<a 

className="dropdown-link" 

href="#" 

onClick={logoutClickHandler} 

> 

Logout 

</a> 

</Menu.Item> 

</Menu.Items> 
 
This creates the menu bar for the page and then from there you create the onClick ={logoutClickHandler}  
 
that includes 
 
const logoutClickHandler = () => { 

Cookies.remove('cart'); 

dispatch({ type: 'CART_RESET' }); 

signOut({ callbackUrl: '/login' }); 

}; 
 
4. import Link from 'next/link'; 

import React from 'react'; 

 
 

export default function DropdownLink(props) { 

let { href, children, ...rest } = props; 

return ( 

<Link href={href}> 

<a {...rest}>{children}</a> 

</Link> 

); 

} 

5. Then go to cart reset and create the reset paramaters and then apply all blue to the a tag and then go from there 
 
case 'CART_RESET': 

return { 

...state, 

cart: { 

cartItems: [], 

shippingAddress: { location: {} }, 

paymentMethod: '', 

}, 

}; 

default: 

return state; 

} 

} 

 
Create Shipping Screen 
1.Create shipping screen 
2. Import Layout title Shipping Address and add checkoutwizard active step 1 and then add checkout wizard 
3.Add the {['User Login', 'Shipping Address', 'Payment Method', 'Place Order'].map( 

4.Then we add a step to create the header/border 
 
5.Then we create the react hook w/ the use form and then add the fullName, shipping address, etc section to the page so this way user can insert their data 
 
6.Make sure you have a submit handler and dispatch then go to the Cart Reset to add the return state cart etc. 
 
case 'SAVE_SHIPPING_ADDRESS': 

return { 

...state, 

cart: { 

...state.cart, 

shippingAddress: { 

...state.cart.shippingAddress, 

...action.payload, 

}, 

}, 

}; 

default: 

return state; 

} 

 
7.Create use effect and setvalue and also get cookies from set cookie 
 
8. Go to initial state and add it to the store.js 
 
9. Go to App.js and create a auth and children 
 
 

function Auth({ children }) { 

const router = useRouter(); 

const { status } = useSession({ 

required: true, 

onUnauthenticated() { 

router.push('/unauthorized?message=login required'); 

}, 

}); 

if (status === 'loading') { 

return <div>Loading...</div>; 

} 

 
 

return children; 

} 

 
10. Add component and auth component auth to the page 
{Component.auth ? ( 

<Auth> 

<Component {...pageProps} /> 

</Auth> 

) : ( 

<Component {...pageProps} /> 

)} 
 
11. At the end of the page add shipping screen.auth = true 
 
12.Then create an unauthorized page where we display a non valid query 
 
13. import { useRouter } from 'next/router'; 

import React from 'react'; 

import Layout from '../components/Layout'; 

 
 

export default function Unauthorized() { 

const router = useRouter(); 

const { message } = router.query; 

 
 

return ( 

<Layout title="Unauthorized Page"> 

<h1 className="text-xl">Access Denied</h1> 

{message && <div className="mb-4 text-red-500">{message}</div>} 

</Layout> 

); 

} 

 
 

14.Push the people to the router function 
 
