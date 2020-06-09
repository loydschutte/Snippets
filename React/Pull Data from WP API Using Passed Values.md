import React, { Component } from 'react';

class Pages extends Component {
    constructor(props) {
        super(props);
        console.log('Inside constructor')
        this.state = {
            pageContent: "",
            pageTitle: "",
            pageImage: "",
            dataId: this.props.id,
        };// this.state
    }// constructor

    componentDidMount() {
        var dataId = this.props.id;
        let dataURL = "http://neverboring.com.s219631.gridserver.com/wp-json/wp/v2/hps-api/" + dataId +"?_embed"
        console.log(dataURL);
        const myHeaders = new Headers({
            'Content-Type': 'text/plain'
        }); // myHeaders
        fetch(dataURL, myHeaders)
            .then(data => data.json())
            .then(data => {
                this.setState ({
                    pageTitle: data.section_title,
                    pageContent: data.content.rendered,
                    pageImage: data._embedded['wp:featuredmedia'][0].media_details.sizes["full"].source_url,
                    pageImagetitle: data._embedded['wp:featuredmedia'][0].title.rendered

                });// this.state
            });// promise
    }// componentDidMount
    render() {
        if(!this.state.pageContent) return <p>Loading. . .</p>;
        return <article className='printed'>
            <div className='container'>
                <div className='row align-items-center'>
                    <div className='col-lg-8 offset-lg-2 text-center'>
                        <img className='img-responsive' src={this.state.pageImage} alt={this.state.pageImagetitle}/>
                        <h3>{this.state.pageTitle}</h3>
                        <div className="post-content" dangerouslySetInnerHTML={{__html: this.state.pageContent}}></div>
                    </div>
                </div>
            </div>
        </article>;
    }// class
}// constructor

export { Pages };