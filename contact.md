---
layout: page
title: Contact
permalink: /contact/
---

<p>You can reach me at <a href="tel:+381-64-928-0460">+381 (64) 928-0460</a> and make an appointment.</p>

<p>The office I work at is open from &#x1f558;&nbsp; <strong>9:00AM</strong> up to <strong>6:00PM</strong> from Monday to Friday. We are closed during the weekend.</p>

<p>The office is located at Vojvode Stepe 107 in Belgrade, Serbia.</p>

<iframe class="google-maps" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2832.0604326695534!2d20.47106441588275!3d44.77957328688286!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x475a705cedc4e2ad%3A0x27d479ecca1d6310!2sEsseWorks!5e0!3m2!1sen!2srs!4v1461070741137" width="100%" height="280" frameborder="0" style="border:0" allowfullscreen></iframe>

<h2>Write me a message:</h2>

<form id="contactForm" action="https://getsimpleform.com/messages?form_api_token=efcacb7ec51952d0f2b8515a79d22623" method="post">
  <div class="form-control">
    <input id="email" type="email" name="email" placeholder="Your email address"/>
  </div>
  <div class="form-control">
    <textarea id="message" name="message" placeholder="Your message"></textarea>
  </div>
  <div class="form-control">
    <input type="submit" value="SEND" />
  </div>
</form>

<div id="messageSent">
  <h2>Your message has been sent successfully!</h2>
  <p>I will get back to you within one business day.</p>
</div>

<h2>Company</h2>

<ul>
  <li>Business name: <a href="http://pretraga2.apr.gov.rs/EnterpreneurPublicWebSearch/Details/EnterpreneurAddressData/6902130?code=BB6B6CF6FFDB630D321CCC97BA034663AB850062">MARKO SANKOVIĆ PR MALI NERED</a></li>
  <li>Identification number: 63468754</li>
  <li>Head office: Matice Srpske 57, Belgrade</li>
</ul>

<script type="text/javascript">
(function() {

  var form = document.getElementById('contactForm');

  if (localStorage.getItem('sent')) {
    form.parentElement.removeChild(form);
    var messageSent = document.getElementById('messageSent').style.display = 'block';
    localStorage.removeItem('sent');
  }

  form.onsubmit = function(e) {

    // Prevent form from submitting unless email and message are valid.
    e.preventDefault();

    // Elements.
    var email = document.getElementById('email');
    var message = document.getElementById('message');

    // Validation.
    if (email.value == '') {
      alert('Email is empty!');
      return;
    }

    if (message.value == '') {
      alert('Message is empty!');
      return
    }

    // Email and message are valid. Submit form.
    localStorage.setItem('sent', true);
    this.submit();
  };
})();
</script>
