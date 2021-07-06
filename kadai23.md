@startuml
entity "顧客マスタ" as customer <m_customers>
<<M,MASTER_MARK_COLOR>>{
  +customer_code[PK]
  --
  pass
  name
  addrress
  tel
  mail
  del_flag
  reg_date
  }
  
  entity "購入テーブル" as purchase<d_purchase>
  <<T,>>{
  +order_id[PK]
  --
  # customer_code[FK]
  purchase_date
  total_price
  }
  
  entity "購入詳細テーブル" as purchase_date<d_ purchase_date>
  <<t,>>{
  +order_id[PK]
  --
  +detail_id[PK]
  --
  # item_code[FK]
  price
  num
  }
  
  entity "商品マスタ" as items <m_items>
  <<M,>>{
  +items_code[PK]
  --
  item_name
  price
  # category_id[FK]
  image
  detail
  del_flag
  reg_date
  }
  
  entity "カテゴリマスタ" as category <m_category>
  <<M,>>{
+category_id[PK]
--
name
reg_date
}

顧客マスタ|〇..〇{購入テーブル
購入テーブル||..|{購入詳細テーブル
購入詳細テーブル{--||items
商品マスタ〇{--||カテゴリマスタ
@enduml

