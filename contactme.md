---
layout: page
title: Contact Me

---

  <section id="contact" class="contact">
      
  <div class="container" data-aos="fade-up">

  <div class="section-title text-center ">
          <h2>Get In Touch</h2>
  </div>

   <div class="row mt-1  shadow p-3 mb-5 bg-white rounded">

   <div class="col-lg-4">
            <div class="info">
              <div class="address">
                <h4>Location:</h4>               
                <p>{{site.location}}</p>
              </div>

   <div class="email">
               <h4>Email:</h4>
                <p><a href="mailto: kumar.amit14595@gmail.com" class="anchor">{{site.email}}</a></p>
              </div>

   <div class="phone">
                <h4>Call:</h4>           
                <p>{{site.contact}}</p>
   </div>

  <div class="phone">
                <h4>Timings:</h4>
                <p>11 am to 6 pm</p>
   </div>
   </div>
   </div>
   
   <div class="col-lg-8 mt-5 mt-lg-0">
  
  <form action="https://send.pageclip.co/FNW4UpfQ0in4CTOdsMvu3792wK6mYmY5/QueryContact" class="email-form" method="post">
              <div class="form-row">
                <div class="col-md-6 form-group">
                  <input type="text" name="name" class="form-control" id="name" placeholder="Your Name" data-rule="minlen:4" data-msg="Please enter at least 4 chars" />
                  <div class="validate"></div>
                </div>
                <div class="col-md-6 form-group">
                  <input type="email" class="form-control" name="email" id="email" placeholder="Your Email" data-rule="email" data-msg="Please enter a valid email" />
                  <div class="validate"></div>
                </div>
              </div>
              <div class="form-group">
                <input type="text" class="form-control" name="subject" id="subject" placeholder="Subject" data-rule="minlen:4" data-msg="Please enter at least 8 chars of subject" />
                <div class="validate"></div>
              </div>
              <div class="form-group">
                <textarea class="form-control" name="message" rows="5" data-rule="required" data-msg="Please write something for us" placeholder="Message"></textarea>
                <div class="validate"></div>
              </div>
              <div class="text-center mb-3"><button type="submit" class="btn btn-success">Send Message</button></div>
            </form>

   </div>

   </div>

   </div>
   </section>