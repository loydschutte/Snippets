.arrow:hover:before{
		    content: "";
		    display: block;
		    width: 0px;
		    height: 0px;
		    border-top: 10px solid transparent;
		    border-bottom: 10px solid transparent;
		    border-left: 14px solid rgba(217,189,107,100);
		    position: absolute;
		    left: -18px;
		}
		
		Add .arrow class to an <li> to have show indicator arrow on hover. It's VERY important to have the positioning, content and display set. border-left changes the width and color of the arrow. left changes the offset.