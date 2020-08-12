# SEO traktor

## API Documentation

The API explantation and usages.

### Authentication (API Keys)
Всеки рекуест трябва да садържа `api_token` който е с дължина 32. <br>
Пример: `GET SITE/api/v1/keywords {api_token: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, ...}` <br> <br>
<b> Параметри на рекуеста </b> <br>

#### Keywords
`GET /api/v1/keywords`

<table>
    <thead>
        <tr>
            <th>Параметър</th>
            <th>Тип</th>
            <th>Описание</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>include_poor</td>
            <td><code>(bool)</code> - Default <code>false</code> </td>
            <td>Връща всички думи включително и тези които не са одобрени</td>
        </tr>
    </tbody>
</table>

#### Posts
`GET /api/v1/aida_posts`


<table>
    <thead>
        <tr>
            <th>Параметър</th>
            <th>Тип</th>
            <th>Описание</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>include_poor</td>
            <td><code>(bool)</code> - Default <code>false</code> </td>
            <td>Връща всички изречения включително и тези които не са одобрени</td>
        </tr>
    </tbody>
</table>


## PHP wrapper class

#### Usage:
````
include 'SeoTraktor.php';
use Seo\SeoTraktor;

$seo = new SeoTraktor($apiToken);

$approved_posts = $seo->getPosts();
$all_posts = $seo->getPosts(true); // All posts (approved and not approved)
````

#### Fields:

##### Post
````
'id'
'text'
'industry_id'
'keyword_id'
'parent_id'
'created_at'
'updated_at'
'deleted_at'
'client_id'
'approved'
'title'
````
##### Keyword
````
'id'
'keyword'
'industry_id'
'money_rank'
'created_at'
'updated_at'
'deleted_at'
'crap_id'
'level'
'bot_ranking'
'admin_accepted'
'parent_keyword_id'
'searched_for_bottom_suggestions'
'searched_for_related_kws'
````

#### Make posts as taken
When an post is taken (when is saved in your database), You must make it as taken. So this post will not be returned by the API again. You need to do that bacause in the future the API can return new freshly created posts for you. So you don't need to see the posts that you already have taken.

##### Simple usage - without future statistics</b>
````
// Mark the posts as taken in our databse. list only the ids of the posts you have taken in an array.

$seo->markPostsAsTaken([189, 190, 193, 197, ...]);
````

##### Advanced usage with options (our service can provide statistics / ranking data and or another features in the future)</b>
````
$seo->markPostsAsTaken([
  ['id' => 189, 'publish_date' => '2020-08-12 13:32:39'],
  ['id' => 190, 'publish_date' => '2020-08-13 15:35:11'],
  ...
]);
````
