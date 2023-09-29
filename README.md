# faq


  <!--/ By dfeault the answers are hidden and jquery used below will toggle on click-->
<div class="full-fq {{ section.settings.class }}">
 {% if section.settings.title != blank %}
      <div class="page-width">
        <div class="title-holder">
          <h2>{{ section.settings.title | escape }}</h2>
        </div>
      </div>
  {% endif %}

<div class=" page-width" data-section-id="{{ section.id }}">
  {% if section.blocks.size > 0 %}
    <div class="faq-wrapper">
        {% for block in section.blocks %}
            {% case block.type %}
          {% when 'faqheader' %}
          <h3 class="faq_page_subheader">{{ block.settings.faqheader }}</h3>
           {% endcase %}
          <div class="faq--{{ block.id }}" {{ block.shopify_attributes }}>
            <div class="faq-individual">
              {% if block.settings.question != blank %}
              <div class="faq-question {% if forloop.index == 1 %} first_oppn {% endif %}">{{ block.settings.question }} <span><i class="fa fa-plus"></i></span></div>
              {% endif %}
              {% if block.settings.answer != blank %}
                <div class="faq-answer">{{ block.settings.answer }}</div>
              {% endif %}
            </div>
          </div>
        {% endfor %}
    </div>
  {% endif %}

  {% if section.blocks.size == 0 %}
    {% include 'no-blocks' %}
  {% endif %}
  <!--/ Extra info to showcase like if you don't find contact us to this email address -->
  {% if section.settings.faq_footer_title != blank %}
  	<div class="faq-footer-title"><h3>{{ section.settings.faq_footer_title }}</h3></div>
  {% endif %}
  
  {% if section.settings.faq_footer_email != blank %}
  	<div class="faq-footer-email"><a href="mailto:{{ section.settings.faq_footer_email }}">{{ section.settings.faq_footer_email }}</a></div>
  {% endif %}
  
</div>
</div>
{% schema %}
  {
    "name": "FAQ",
    "class": "index-section",
    "settings": [
      {
        "type": "text",
        "id": "class",
        "label": "Custom Class"
 
      },
      {
        "type": "text",
        "id": "title",
        "label": "FAQ page heading",
        "default": "FAQ"
      }
    ],
    "blocks": [
       {
    "type": "faqheader",
	"name": "FAQ Split Header",
	"settings": [
	  {
	    "type":"text",
		"id": "faqheader",
		"label": "FAQ Header Splitter"
	  }
      ]
  },
      {
        "type": "text_block",
        "name": "Item",
        "settings": [
          {
            "type": "text",
            "id": "question",
            "label": "Question",
            "default": "Add Question"
          },
          {
            "type": "richtext",
            "id": "answer",
            "label": "Add answer",
            "default": "<p>Add Answer</p>"
          }
        ]
      }
    ],
    "presets": [
      {
        "name": "FAQ",
        "category": "Text",
        "blocks": [
          {
            "type": "faqheader"
          },
          {
            "type": "text_block"
          },
          {
            "type": "text_block"
          },
          {
            "type": "text_block"
          }
        ]
      }
    ]
  }
{% endschema %}

   // faq js
  $('.faq-question').click(function(){
  $(this).siblings('.faq-answer').slideToggle();
    $(this).parent().toggleClass('open-state');
    if($(this).find('.fa').hasClass('fa-plus')){
      $(this).find('.fa').removeClass('fa-plus');
      $(this).find('.fa').addClass('fa-minus');
    }else if($(this).find('.fa').hasClass('fa-minus')){
      $(this).find('.fa').removeClass('fa-minus');
      $(this).find('.fa').addClass('fa-plus');
    }
});

      // For first tab open
   $('.first_oppn').trigger('click');

/*faq css*/
.faq-answer{display:none;}
  .faq-question {
    font-size: 18px;
    font-weight: bold;
    margin-top: 12px;
    
    padding: 20px;
    
    cursor: pointer;
}.faq-question span {
    display: inline-block;
    float: right;
    height: 25px;
    width: 25px;
    background: #bdbdbd;
    text-align: center;
    border-radius: 50%;
    text-align: center;
    color: white;
}
.faq-wrapper .faq-question span i {
   text-stroke: 1px #bdbdbd;
   -webkit-text-stroke: 1px #bdbdbd;
   -moz-text-stroke: 1px #bdbdbd;
   -ms-text-stroke: 1px #bdbdbd;
   font-size: 15px;
}.faq-wrapper .faq-question span {
   line-height: 23px;
}
.left_form.grid__item select.field__input {
    border: 1px solid #ddd;
    padding: 0px 20px;
}

.slider-mobile-gutter .banner {
    margin-top: 2rem !important;
}


.field.select-arrow {
    position: relative;
}

.field.select-arrow:before {
    content: "\f078";
    position: absolute;
    right: 20px;
    left: auto;
    font-family: fontAwesome;
    font-size: 12px;
    top: 32px;
    z-index: 1;
}
section#shopify-section-template--20611180101921__c5dacda8-4be3-4e8a-aacb-202c9ab6e762 {
    padding-top: 5rem !important;
}
