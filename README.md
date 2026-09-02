
# VYBE

### A Social Fitness Platform

VYBE is a social fitness platform designed to connect people through their gym community.

Users can share photos, short videos, stories, blogs, discover people at their gym, chat with other members, and explore gym information and membership plans.

The platform is designed with a social-media-first experience inspired by modern platforms such as Instagram and Snapchat.

---

## Features

### Social Feed
- Share fitness photos
- Share short videos
- Like posts
- Comment on posts
- Share and save content
- Personalized feed

### Stories
- Upload photos and short videos
- Add captions and creative elements
- Stories expire after 24 hours
- View stories from friends and gym members

### Profiles
- User profiles
- Profile photos
- Posts and videos
- Followers and following
- Fitness interests
- Gym information

### Meet People
- Discover people from your gym
- Find workout partners
- Connect with gym members
- Follow users
- Send messages

### Messaging
- One-to-one chat
- Send text messages
- Share photos and videos
- Real-time messaging
- Read status

### Blogs
- Create fitness blogs
- Add images and videos
- Like and comment on blogs
- Discover blogs from other users

### Gym
- Gym profiles
- Gym members
- Gym photos and posts
- Membership plans
- Gym information

---

# High-Level Design

## System Architecture

```text
                         ┌─────────────────────┐
                         │      VYBE USER      │
                         │  Mobile / Desktop   │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │      FRONTEND       │
                         │   React / Next.js   │
                         │     Tailwind CSS    │
                         └──────────┬──────────┘
                                    │
                              HTTPS / REST
                                    │
                                    ▼
                  ┌─────────────────────────────────┐
                  │             BACKEND             │
                  │        Node.js + Express        │
                  │                                 │
                  │  ┌─────────┐ ┌──────────────┐  │
                  │  │  Auth   │ │ Social       │  │
                  │  │ Service │ │ Service      │  │
                  │  └─────────┘ └──────────────┘  │
                  │                                 │
                  │  ┌─────────┐ ┌──────────────┐  │
                  │  │ Content │ │ Chat Service │  │
                  │  │ Service │ │  WebSocket   │  │
                  │  └─────────┘ └──────────────┘  │
                  │                                 │
                  │  ┌─────────┐ ┌──────────────┐  │
                  │  │  Gym    │ │ Notification │  │
                  │  │ Service │ │ Service      │  │
                  │  └─────────┘ └──────────────┘  │
                  └──────────────┬──────────────────┘
                                 │
                 ┌───────────────┼─────────────────┐
                 │               │                 │
                 ▼               ▼                 ▼
          ┌────────────┐  ┌─────────────┐  ┌──────────────┐
          │ PostgreSQL │  │    Redis    │  │  Cloudinary  │
          │  Database  │  │ Cache/Live  │  │ Photos/Videos│
          └────────────┘  └─────────────┘  └──────────────┘
