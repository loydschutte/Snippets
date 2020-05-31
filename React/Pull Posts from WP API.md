import React, { Component } from 'react';
import Moment from 'react-moment';

class Posts extends Component {
    constructor() {
        super();
        this.state = {
            posts: []
        }
    }


    componentDidMount() {

        let dataURL = "http://yourwordpressserver.com/wp-json/wp/v2/posts?_embed";
        fetch(dataURL)
         .then(res => res.json())
         .then(res => {
           this.setState({
             posts: res
         })
       })
   } /* componentDidMount */

    render() {
       let posts = this.state.posts.map((posts, index) => {
         return(
            <article id={posts.id} key={index} className='blog-post col-lg-6'>
             {posts.featured_media ?
                 <div className='post-image'>
                <img className='img-responsive' src={posts._embedded['wp:featuredmedia'][0].media_details.sizes["full"].source_url} alt={posts.title}/>
                </div>
             : null}

            <h3>{posts.title.rendered}</h3>
            <div className='post-date'><Moment format="MMMM Do YYYY">{posts.date_gmt}</Moment></div>
             <div className='post-content' dangerouslySetInnerHTML={{__html:posts.excerpt.rendered}}></div>
                </article>
            ) /* return */
        }); /* let */
        return (
            <section>
               {posts}
            </section>
        ) /*return*/
    } /* render */
} /* class */
export default Posts;

