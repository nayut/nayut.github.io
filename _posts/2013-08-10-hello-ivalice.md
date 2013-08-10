---
layout: post
title: "Hello Ivalice."
description: ""
category: 
tags: []
---
{% include JB/setup %}

ファイナルファンタジータクティクスの世界を通じて、RubyとRuby on Railsをはじめとする技術を身につけていきます。

![FFT](/img/20130810_whitemage.png)

#### アプリケーションの作成
    $ rails new fft

#### サーバ起動
    $ rails s

#### 動作確認
    http://localhost:3000/

#### scaffold
    $ rails generate scaffold ability job:string name:string mp:integer speed:integer jp:integer

使える型
http://whitech0c0late.hatenablog.com/entry/2012/09/07/183229

#### migrate
    $ rake db:migrate

#### 動作確認
    http://localhost:3000/abilities

#### 試しにデータ作成
New Abilityリンクから手入力します。

* Job: 白魔道士, Name: ケアル, Mp: 6, Speed: 25, Jp: 50
* Job: 白魔道士, Name: ケアルラ, Mp: 10, Speed: 20, Jp: 180

#### 一括取込用のCSVファイルを作成
/fft/db/seeds_data/whitemage.csv
<pre>
白魔道士,ケアル,6,25,50
白魔道士,ケアルラ,10,20,180
白魔道士,ケアルガ,16,15,450
白魔道士,ケアルジャ,20,10,800
白魔道士,レイズ,10,25,200
白魔道士,アレイズ,20,10,600
白魔道士,リレイズ,16,15,1000
白魔道士,リジェネ,8,25,350
白魔道士,プロテス,6,25,70
白魔道士,プロテジャ,24,15,600
白魔道士,シェル,6,25,70
白魔道士,シェルジャ,20,15,600
白魔道士,ウォール,24,25,400
白魔道士,エスナ,18,34,300
白魔道士,ホーリー,56,17,600
</pre>

#### seeds.rbの編集
/fft/db/seeds.rb

	# coding: utf-8
	require "csv"

	Ability.delete_all
	CSV.foreach('db/seeds_data/whitemage.csv') do |row|
	  Ability.create(:job => row[0], :name => row[1], :mp => row[2], :speed => row[3], :jp => row[4])
	end

#### 初期データとして投入
	$ rake db:seed

#### 動作確認
    http://localhost:3000/abilities
