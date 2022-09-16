<template>
  <html>
    <div id="appmain" class="lg:m-0 lg:pl-324px">
      <link
        href="https://unpkg.com/boxicons@2.0.7/css/boxicons.min.css"
        rel="stylesheet"
      />
      <Nav />
      <main class="bg-black w-full xl:ml-4">
        <Home :developmentMode="false" />
        <About :siteData="siteData" :tools="tools" />
        <Services />
        <Works />
        <Contact />
      </main>
    </div>
  </html>
</template>

<script>
import gql from "graphql-tag";
const SITE_DATA_QUERY = gql`
  query MyQuery {
    siteData(where: { siteDataSlug: "sitedata" }) {
      aboutMe
      profileImage {
        url
      }
      resumeLink {
        url
      }
      developmentMode
    }
  }
`;

const ALL_TOOLS_QUERY = gql`
  query MyQuery {
    tools {
      name
      image {
        url
      }
      id
    }
  }
`;
export default {
  data() {
    return {
      siteData: {
        profileImage: {
          url: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8Mnx8cHJvZmlsZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=400&q=60",
        },
        aboutMe: "",
        resumeLink: {
          url: "Google.com",
        },
      },
      tools: [
        {
          id: "1",
          image: {
            url: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8Mnx8cHJvZmlsZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=400&q=60",
          },
          name: "Vue",
        },
      ],
      error: null,
    };
  },
  apollo: {
    siteData: {
      query: SITE_DATA_QUERY,
      prefetch: true,
      error(error) {
        this.error = JSON.stringify(error.message);
      },
    },
    tools: {
      query: ALL_TOOLS_QUERY,
      prefetch: true,
      error(error) {
        this.error = JSON.stringify(error.message);
      },
    },
  },
};
</script>

html{ scroll-behavior: smooth; }
