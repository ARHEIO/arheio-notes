---
title: Forestry and the Dev Blog

---
# the dev blog

I was tired of having all my notes scattered over a bunch of places, so I started this site as a way to collate them.

At its base it's a NextJS app that renders Markdown files.

Those Markdown files are edited using forestry.io and published to another GitHub repo. Images meanwhile are published to an S3 bucket.

The NextJS backend pulls those files and exposes them via Fastify + GraphQL to the NextJS frontend.