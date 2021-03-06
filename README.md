## 概述
此套件供 GitHub API 讀取。

## 基本
```PHP
$github = new \Memo\Github();

$github
    // 設置 HTTP 請求目標
    ->request('[repos/users]', '[name]', '[target]')
    // 設置 HTTP 請求選項
    ->option([
        'headers' => [
            // 認證
            'Authorization' => 'token [personal API token]',
            // 文本格式
            'Accept' => '[media type]'
            ]
    ])
    // 分頁
    ->paginate([per_page], [page])
    // 顯示錯誤訊息
    ->showException();

// 取得 HTTP 響應 Body
var_dump($github->getBody());

// 取得 HTTP 響應 Header Line
var_dump($github->getHeaderLine('[header line]'));
```

## 範例
### 設置 HTTP 請求目標
```PHP
// 取得 laravel/laravel 儲存庫
$github->request('repos', 'laravel/laravel');

// 取得 laravel/laravel 儲存庫的所有 contributors
$github->request('repos', 'laravel/laravel', 'contributors')

// 取得 memochou1993 使用者
$github->request('users', 'memochou1993')

// 取得 memochou1993 使用者的所有 followers
$github->request('users', 'memochou1993', 'followers')
```

### 設置 HTTP 請求選項
```PHP
$github->option([
    'headers' => [
        // 認證
        'Authorization' => 'token 84411234372912342f351234dc9712343b301234',
        // 文本格式
        'Accept' => 'application/vnd.github.mercy-preview+json'
        ]
]);
```

### 分頁
```PHP
// 每頁顯示 10 筆，讀取第 1 頁
$github->paginate();

// 每頁顯示 20 筆，讀取第 1 頁
$github->paginate(20, 1);
```

### 顯示錯誤訊息
```PHP
// 顯示來自 GitHub API 的錯誤訊息
$github->showException();
```

### 取得 HTTP 響應
```PHP
// 取得 HTTP 響應 Body
$github->getBody();

// 取得 HTTP 響應 Header Line 的 X-RateLimit-Remaining
$github->getHeaderLine('X-RateLimit-Remaining');
```