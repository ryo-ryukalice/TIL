# omniauth-line で別 provider のユーザーを LINE に移動する

`/auth/line` に認証用のクエリパラメーターを付与しておけば、callback で `request.env['omniauth.params']` に戻してもらえるので、適当な認証用トークンを使って callback で認証する。

view
```erb
<%= link_to 'LINEに移行', "/auth/line?token=#{current_student.token}" %>
```

callback controller
```rb
User.find_by!(token: request.env['omniauth.params']['token']).update!(
  provider: auth_params['provider'],
  uid: auth_params['uid']
)
redirect_to mypage_path, notice: '今後は LINE ログインを利用してください。'
```
