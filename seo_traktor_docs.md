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
