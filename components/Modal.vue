<template>
  <transition name="fade">
    <div class="modal-container">
      <div class="overlay" @click="toggleModal"></div>
      <div class="modal">
        <div class="close-container">
          <p>About</p>
          <div class="icon-close" @click="toggleModal"></div>
        </div>
        <p>
          I believe that design works on the mind through the eyes. In the right
          context, with the right tone of voice, graphic design has the ability
          to spark emotion, engage the imagination and even, at its best,
          inspire action.
        </p>
        <p>
          I’m Andy Stewart, a Creative Director and Designer based in Seattle.
          I’ve spent the last ten years helping to bring life to brands through
          strategic, thoughtful design.
        </p>
        <p>
          As a generalist by both training and predilection, I'm well versed in
          translating visions, notions and ideas into full-blown realities
          across a variety of media, from brand identities to digital
          experiences.
        </p>
        <a href="mailto:andy.stewart1170@gmail.com">
          <p>Get in Touch</p>
          <div class="arrow">
            <icon-base size="12"><arrow-out /></icon-base>
          </div>
        </a>
      </div>
    </div>
  </transition>
</template>

<script>
import IconBase from '@/components/IconBase'
import ArrowOut from '@/components/icons/ArrowOut'

export default {
  name: 'Modal',
  components: {
    IconBase,
    ArrowOut,
  },
  data() {
    return {
      showModal: true,
    }
  },
  methods: {
    toggleModal() {
      this.$emit('toggle-modal')
    },
  },
}
</script>

<style scoped lang="scss">
@use '@/assets/_base/mixins';

p {
  position: relative;
  margin-bottom: 1rem;
}

a {
  display: inline-flex;
  align-items: center;
  margin-top: 1rem;

  p {
    margin-right: 0.5rem;
    margin-bottom: 0rem;
  }

  .arrow {
    position: relative;
    width: 12px;
    height: 12px;

    svg {
      fill: var(--white);
    }
  }
}

.modal-container {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
  z-index: 1000000;

  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: var(--black);
    opacity: 0.85;
  }

  .modal {
    position: absolute;
    top: 0;
    right: 0;
    height: 100vh;
    width: 100%;
    max-width: 480px;
    padding: 1.25rem;
    background: var(--blue);
    color: var(--white);
    box-shadow: -1px 0px 15px 0px rgba(0, 0, 0, 0.6);
    font-size: 0.875rem;

    @include mixins.respond(md) {
      font-size: 1rem;
    }

    .close-container {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      width: 100%;
      margin-bottom: 1rem;

      p {
        margin: 0;
      }

      .icon-close {
        position: relative;
        width: 2.5rem;
        height: 2.5rem;
        background: rgba(0, 0, 0, 0);
        border-radius: 50%;
        cursor: pointer;
        transition: all 0.5s cubic-bezier(0.33, 1, 0.68, 1);

        &::before,
        &::after {
          content: '';
          position: absolute;
          top: 50%;
          left: 50%;
          width: 1rem;
          height: 1px;
          background: var(--white);
          transform: translate3d(-50%, -50%, 0) rotate(45deg);
          transition: transform 0.5s cubic-bezier(0.33, 1, 0.68, 1);
        }

        &::after {
          transform: translate3d(-50%, -50%, 0) rotate(-45deg);
        }

        &:hover {
          transform: rotate(90deg);
          background: rgba(0, 0, 0, 0.5);
          box-shadow: inset 0px 1px 8px 0px rgba(0, 0, 0, 0.6);

          &::before,
          &::after {
            transform: translate3d(-50%, -50%, 0) rotate(90deg);
          }
        }
      }
    }
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s cubic-bezier(0.22, 1, 0.36, 1);
  transition-delay: 0;

  .overlay {
    pointer-events: none;
  }

  .modal {
    transform: translate3d(0%, 0, 0);
  }
}

.fade-enter-to,
.fade-leave {
  .modal {
    transition: transform 0.5s cubic-bezier(0.33, 1, 0.68, 1);
    transition-delay: 0.5s;
  }
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transition: opacity 0.5s;
  transition-delay: 0.5s;

  .modal {
    transform: translate3d(100%, 0, 0);
    transition: transform 0.5s cubic-bezier(0.32, 0, 0.67, 0);
    transition-delay: 0s;
  }
}
</style>
