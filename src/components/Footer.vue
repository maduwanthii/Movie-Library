<template>
  <footer>
    <div class="ui-top">
      <div class="ui-top-companyname">Amadeus IT Group</div>
      <div class="social-follow">
        <div class="social-inline">
          <p class="follow-text">Follow us on</p>
          <img src="/assets/Icons/Twitter White.svg" alt="Twitter" />
          <img src="/assets/Icons/Youtube White.svg" alt="YouTube" />
        </div>
      </div>
    </div>

    <div class="address">
      <p>C. Salvador de Madariaga, 1</p>
      <p>28027 Madrid</p>
      <p>Spain</p>
    </div>

    <hr class="footer-divider" />

    <div class="footer-bottom">
      <div class="footer-left">
        <p>
          Copyright © {{ currentYear }} Amadeus Hotels. All rights reserved.
        </p>
      </div>
      <div class="footer-right">
        <p>
          Photos by
          <span class="underline">Felix Mooneeram</span> &amp;
          <span class="underline">Serge Kutuzov</span> on
          <span class="underline">Unsplash</span>
        </p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  computed: {
    currentYear() {
      return new Date().getFullYear();
    },
  },
};
</script>

<style scoped>
footer {
  background: #151515;
  color: white;
  padding: 0.5rem 1.5rem;
  font-size: 0.9rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.ui-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

.ui-top-companyname {
  font-family: "Arial Black", Arial, sans-serif;
  font-size: 12px;
  font-weight: bold;
}

.address {
  text-align: left;
  font-size: 12px;
  font-family: "Lucida Sans Unicode", "Lucida Grande", "Lucida Sans", Geneva,
    Verdana, sans-serif;
}
.address p {
  margin: 2px 0;
  line-height: 1.2;
}

.social-follow {
  text-align: right;
}
.social-inline {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.follow-text {
  margin: 0;
  font-family: "Lucida Sans Unicode", "Lucida Grande", "Lucida Sans", Geneva,
    Verdana, sans-serif;
  font-size: 12px;
}
.social-inline img {
  width: 24px;
  height: 24px;
}

.footer-divider {
  border: none;
  border-top: 0.5px solid #555;
  margin: 0;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  font-size: 0.75rem;
}
.footer-left {
  text-align: left;
}
.footer-right {
  text-align: right;
}

.footer-bottom p {
  font-family: "Lucida Sans Unicode", "Lucida Grande", "Lucida Sans", Geneva,
    Verdana, sans-serif;
  font-size: 11px;
  margin: 0;
}

.underline {
  text-decoration: underline;
}

@media (max-width: 600px) {
  footer {
    text-align: center;
    align-items: center;
  }

  .ui-top {
    flex-direction: column;
    align-items: center;
  }

  .social-follow {
    text-align: center;
  }

  .address {
    text-align: center;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    text-align: center;
  }

  .footer-left,
  .footer-right {
    text-align: center;
  }

  .footer-left p,
  .footer-right p {
    line-height: 1.4;
  }
}
</style>
