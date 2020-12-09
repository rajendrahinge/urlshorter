<template>
<div class="container-fluid">
	<h1>Url shorter</h1>
    <form class="form-inline" action="/action_page.php">
		<div class="form-group">
			<label for="email">Email address:</label>
			<input type="text" v-model="original_url" class="form-control" id="email">
		</div>
		<i @click="submit" class="far fa-paper-plane"></i>
	</form>

	<table class="table">
	<thead>
	  <tr>
	    <th>original url</th>
	    <th>shorten url</th>
	    <th>created at</th>
	  </tr>
	</thead>
	<tbody v-for="item in items" :key="item.id">
	  <tr>
	    <td>{{item.original_url}}</td>
	    <td>{{item.shorten_url}}</td>
	    <td>{{item.created_at}}</td>
	  </tr>
	</tbody>
	</table>
</div>
</template>

<script>
    export default {
    	data() {
    		return {
	    		original_url: "",
	    		error: {},
	    		items: []
    		};
    	},
    	mounted() {
    		this.fetchData();
    	},
        methods : {
        	submit() {
        		if(this.original_url == "") return;  
        		axios.post("/api/url",{original_url:this.original_url}).then(res => {
        			this.original_url = "";
        			this.items.unshift(res.data);
        		}).catch(e => {
        			console.log(e.response)
        		});
        	},
        	fetchData() {
        		axios.get("/api/url").then(res => {
        			this.items = res.data;
        		})
        	}
        }
    }
</script>
