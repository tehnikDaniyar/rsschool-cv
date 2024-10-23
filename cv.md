# Bashirov Daniyar 
## studying front-end development 

--------------------------------------------------
## contants:
- location: Bishkek, Kyrgizstan
- phone: +996505006019
- email: tehnikdaniyar@gmail.com
- GitHub: [tehnikDaniyar](https://github.com/tehnikDaniyar) 
--------------------------------------------------
## about me
I am 39 years old. I currently work as a security and video surveillance engineer. And although I have over 20 years of experience, I want to change my profession to a front-end developer. I completed the stage0 course on the RS School platform.
## skils
- HTML
- CSS
- SASS
- SCSS
- Git
- JavaScript
- Redux
- React
# Code Example
### online cinema site (redux slice with async functions)
[link of this petproject](http://daniyardev.atwebpages.com/)
```
import { createSlice } from '@reduxjs/toolkit'
import { createAsyncThunk } from '@reduxjs/toolkit';
import filmsServices from '../../API/filmsServices';
import axios from "axios";

const baseUrl = 'https://kinopoiskapiunofficial.tech/api/v2.2/films';
const headers = {
	'X-API-KEY': '7c574677-155a-443f-ad27-b7a2b0f8ab9c',
	'Content-Type': 'application/json',
}

export const getFilmsCategories = createAsyncThunk(
	'filmsInfo/getFilmsCategories',

	async function (_, { rejectWithValue, dispatch }) {
		try {
			const response = await axios.get(`${baseUrl}/filters`, {
				headers: headers,
			});
			return await response.data
		} catch (error) {
			console.log(error);
			return rejectWithValue([])
		}
	}
);


export const filmsInfoSlice = createSlice({
	name: 'filmsInfo',
	initialState,
	extraReducers: (builder) => {
		builder
			.addCase(
				getFilmsCategories.fulfilled, (state, actions) => {
					const genres = actions.payload.genres;
					const countries = actions.payload.countries;
					if (Array.isArray(genres) && Array.isArray(countries)) {
						console.log('Categories and countries are Arrayes');
						state.categories = actions.payload.genres ? actions.payload.genres : [];
						state.countries = actions.payload.countries ? actions.payload.countries : [];
					} else {
						console.log('Categories and countries aren`t Arrayes');

						state.categories = [];
						state.countries = [];
					}
				},
				getFilmsCategories.rejected, (state, actions) => {
					state.categories = actions.payload;
					state.countries = actions.payload;
				}
			)
	}
})

```
## english

English language proficiency level: beginner. 
I haven't taken any courses yet, I'm learning on my own. I watch foreign movies without translation. I read documentation for frameworks and libraries (such as swiper, materialUI, swagerAPI and the like) with a dictionary.

