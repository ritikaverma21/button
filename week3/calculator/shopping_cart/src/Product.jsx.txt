import React, { useState } from 'react';

const KIDS_WEAR = 'Kids Wear';
const GIRLSWEAR = 'Girls Wear';

export default function Products({ setCart, cart }) {
  const [products] = useState([
    {
      category: GIRLSWEAR,
      name: 'Pink Full Sweatshirt',
      cost: 15,
      image: 'https://media.vertbaudet.com/Pictures/vertbaudet/110970/pack-of-2-high-neck-tops-for-baby-girls.jpg?width=1320',
      
    },
    {
        category: GIRLSWEAR,
        name: 'Blue Girls Frok',
        cost: 9.0,
        image: 'https://i.pinimg.com/564x/05/ab/1d/05ab1d2511aee91c6f00e54ce7fc6c29.jpg',
      },
      {
        category: GIRLSWEAR,
        name: 'Green Off-Shoulder Top',
        cost: 7.0,
        image: 'https://i.pinimg.com/originals/cd/f7/59/cdf759703dc3f1b4966c6357aded10ad.jpg',
      },
      {
        category: GIRLSWEAR,
        name: 'Black Stylish One Piece',
        cost: 19.0,
        image: 'https://i.pinimg.com/564x/80/39/7e/80397ee54c8d15e1cbb798eee3eb0811.jpg',
      },
      
    {
      category: KIDS_WEAR,
      name: 'Boys Stylish Dress',
      cost: 1066,
      image: 'https://images-na.ssl-images-amazon.com/images/I/51aGvmkJXpL.jpg',
     
    },
    {
        category: KIDS_WEAR,
        name: 'Flower Printed Frok',
        cost: 800,
        image: 'https://image.made-in-china.com/202f0j00OnEQNTiMLyoB/Little-Girls-Clothing-Children-Clothes-Kids-Wear-Dresses-in-Flower-Dress-Frocks.jpg',
      },
      {
        category: KIDS_WEAR,
        name: 'Kids Aishwarya Style Dress',
        cost: 850,
        image: 'https://www.aishwaryadesignstudio.com/content/images/thumbs/0077343_appealing-peach-designer-kids-wear-lehenga-choli-set.jpeg',
      },
      {
        category: KIDS_WEAR,
        name: 'Pink Barbie Style Frok',
        cost: 1000,
        image: 'https://img3.exportersindia.com/product_images/bc-full/2020/2/3021527/kids-party-wear-dress-1582018400-5304201.jpeg',
      },
   
     
  ]);

  const addToCart = (product) => {
    let newCart = [...cart];
    let itemInCart = newCart.find(
      (item) => product.name === item.name
    );
    if (itemInCart) {
      itemInCart.quantity++;
    } else {
      itemInCart = {
        ...product,
        quantity: 1,
      };
      newCart.push(itemInCart);
    }
    setCart(newCart);
  };

  const [category, setCategory] = useState(KIDS_WEAR);

  const getProductsInCategory = () => {
    return products.filter(
      (product) => product.category === category
    );
  };

  return (
    <>
      <h1>Products</h1>
      <b>Select a category </b>
      <select onChange={(e) => setCategory(e.target.value)}>
        <option value={KIDS_WEAR}>{KIDS_WEAR}</option>
        <option value={GIRLSWEAR}>{GIRLSWEAR}</option>
      </select>
      <div className="products">
        {getProductsInCategory().map((product, idx) => (
          <div className="product" key={idx}>
            <h3>{product.name}</h3>
            <h4>${product.cost}</h4>
            <img src={product.image} alt={product.name} />
            <button onClick={() => addToCart(product)}>
              Add to Cart
            </button>
          </div>
        ))}
      </div>
    </>
  );
}