---
layout: post
title:  "The first Blog!"
quote: 端午节
---
# Markdown  从入门----放弃
### 导语：
>写在前面，本文将要指引你入门Markdown，然后指导你放弃者们编辑语言。

#### o(∩∩)o...哈哈

### 开始：
>**粗体语法** 
*斜体语法*
在`PHP`中，使用`echo 'hello world'` 输出 `Hello World`,学习**百度**是本数血红素
asd 
***
#![这时一只狗](http://h.hiphotos.baidu.com/image/h%3D200/sign=e8dfbdc69a16fdfac76cc1ee848e8cea/738b4710b912c8fc8cfeb020fb039245d78821c9.jpg)
	hello

[百度][1]

* 123
+ 2234
- 123

		alter table wms_manifest_in_apply add column reson varchar(255) not null default '' comment '撤销说明';
		insert into wms_system_node (name,node_key,addtime,edittime,remark) values('质检列表','manifestinout@manifestQuality@index',1456209520,1456209520,'手动添加');
		insert into wms_system_node (name,node_key,addtime,edittime,remark) values('申请单质检','manifestinout@manifestQuality@showApply',1456209520,1456209520,'手动添加');
		insert into wms_system_node (name,node_key,addtime,edittime,remark) values('仓单质检','manifestinout@manifestQuality@showManifest',1456209520,1456209520,'手动添加');

		update wms_system_setting set value='{\"system\":{\"modulename\":\"系统\",\"controllers\":{\"settings\":\"系统设置\",\"role\":\"角色管理\",\"node\":\"权限管理\",\"log\":\"日志管理\",\"bSettings\":\"业务设置\",\"admin\":\"帐号管理\"}},\"reposity\":{\"modulename\":\"仓库\",\"controllers\":{\"stock\":\"实时库存\",\"reposity\":\"仓库管理\",\"inventory\":\"库存盘点\",\"check\":\"稽查管理\"}},\"manifestinout\":{\"modulename\":\"出入库\",\"controllers\":{\"manifestOut\":\"出库管理\",\"manifestInApply\":\"入库申请\",\"manifestIn\":\"入库管理\",\"manifestQuality\":\"质检列表\",\"manifestBillOfLading\":\"提货单\"}},\"manifest\":{\"modulename\":\"仓单\",\"controllers\":{\"manifestPriceReview\":\"仓单价格审核\",\"manifestMoveApply\":\"仓单移位申请\",\"manifestMove\":\"仓单移位\",\"manifest\":\"仓单管理\",\"show_split_list\":\"仓单拆分记录\",\"show_merge_list\":\"仓单合并记录\",\"show_personal_change_list\":\"所属人变更记录表\"}},\"company\":{\"modulename\":\"客户\",\"controllers\":{\"companyStock\":\"客户库存\",\"companyBill\":\"客户费用\",\"company\":\"客户管理\"}},\"common\":{\"modulename\":\"公共\",\"controllers\":{\"home\":\"首页\"}},\"account\":{\"modulename\":\"财务\",\"controllers\":{\"list\":\"账单列表\",\"settings\":\"财务设置\",\"manifestout\":\"出库审核\"}}}' where item='module_settings';



		*~~**CREATE OR REPLACE VIEW `wms_stock`*~~**
~~~~

~~FROM~~星期二, 14. 六月 2016 05:04下午 

(
	(
		(
			(
				(
					((
							`manifest` LEFT JOIN `wms_company` `company`
							ON(
								(
									`manifest` . `wms_company_id` = `company` . `id`
								)
							)
						) LEFT JOIN `wms_manifest_storage` `storage`
						ON(
							(
								`manifest` . `id` = `storage` . `manifest_id`
							)
						)
					) LEFT JOIN `wms_manifest_storage_mapping` `map`
					ON(
						(
							`map` . `storage_id` = `storage` . `id`
						)
					)
				) LEFT JOIN `wms_manifest_storage_area` `storagearea`
				ON(
					(
						`storagearea` . `id` = `map` . `storage_area_id`
					)
				)
			) LEFT JOIN `wms_reposity_area` `area`
			ON(
				(
					`area` . `id` = `storagearea` . `area_id`
				)
			)
		) LEFT JOIN `wms_reposity_area` `areabak`
		ON(
			(
				`area` . `parent_area_id` = `areabak` . `id`
			)
		)LEFT JOIN `wms_reposity` `reposity`
		ON(
			(
				`reposity` . `id` = `manifest` . `wms_repository_id`
			)
		)
	)
)
WHERE
(
	(
		`manifest` . `is_cc_manifest` = 1
	)
	AND(
		`storage` . `manifest_status` = 1
	)
)
ORDER BY
`manifest` . `modify_date`;




/******wms_reposity_stock********/
CREATE OR REPLACE VIEW `wms_reposity_stock`
AS (
	SELECT
	`wms_stock` . `reposity_name` AS `reposity_name`,
	`wms_stock` . `number` AS `number`,
	`wms_stock` . `alias_name` AS `alias_name`,
	`wms_stock` . `pkg_size` AS `pkg_size`,
	`wms_stock` . `wms_company_id` AS `wms_company_id`,
	`wms_stock` . `product_name` AS `product_name`,
	`wms_stock` . `is_cc_manifest` AS `is_cc_manifest`,
	`wms_stock` . `brand_number` AS `brand_number`,
	`wms_stock` . `factory_name` AS `factory_name`,
	`wms_stock` . `create_date` AS `create_date`,
	`wms_stock` . `modify_date` AS `modify_date`,
	`wms_stock` . `qty` AS `qty`,
	`wms_stock` . `storage_tel` AS `storage_tel`,
	`wms_stock` . `storage_company_name` AS `storage_company_name`,
	`wms_stock` . `storage_company_user_full_name` AS `storage_company_user_full_name`,
	`wms_stock` . `weight` AS `weight`,
	`wms_stock` . `company_id` AS `company_id`,
	`wms_stock` . `reposity_id` AS `reposity_id`,
	`wms_stock` . `area_id` AS `area_id`,
	`wms_stock` . `kw_id` AS `kw_id`,
	`wms_stock` . `kw` AS `kw`,

	group_concat(
		`wms_stock` . `alias_name`,
		':',
		`wms_stock` . `weight` SEPARATOR ','
	) AS `area`,
	group_concat(
		`wms_stock` . `alias_name` SEPARATOR ','
	) AS `location`
	FROM
	`wms_stock`
	GROUP BY
	`wms_stock` . `number`
);


<table>
    <tr>
        <td>Foo</td>
	<td>Foo</td>
    </tr>
 <tr>
        <td>Foo</td>
	<td>Foo</td>
    </tr>
 <tr>
        <td>Foo</td>
	<td>Foo</td>
    </tr>
</table>

&copy;AT&amp;T 

[1]: http://www.baidu.com/


