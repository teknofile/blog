---
layout: page
short_name: scion
name: Scion xB
title: Scion xB
description: All about my 2006 Scion xB. My second one. What are the plans and how am I tracking at making it very comfortable.
image_logo: ../assets/logo_scionxb.webp
---
<table cellpadding="10">
<tr>
  <td valign="top" align="center"><img src="../assets/logo_scionxb.webp" width="200px" /></td>
  <td align="left" valign="top">
    <h4>About The Scion</h4>
    <p>I recently (in 2024) bought my second 1st Generation Scion xB. I really like the platform.</p>
    <p>Yes, I know it's shaped like a toaster. A brick. A square.</p>
    <strong>I don't care.</strong>
  </td>
</tr>
<tr><td colspan="2" align="center" valign="middle"><hr width="80%" /></td></tr>
<tr>
  <td colspan="2">
    <h4>Posts & Articles</h4>
    <ul>
      {% assign filtered_posts = site.posts | where: 'project', page.short_name %}
      {% for post in filtered_posts %}
        <li><a href="{{ post.url }}"> {{ post.title }}</a></li>
      {% endfor %}
    </ul>
  </td>
</tr>
</table>
