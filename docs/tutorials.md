# Postman Collections

Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet.Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet, Lorem Ipsum Sit Dolor Amet.

## Core - WP SSO.postman_collection

	{
		"info": {
			"_postman_id": "9e06f044-16b3-464b-bd11-4f4121d4320e",
			"name": "Core - WP SSO",
			"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
		},
		"item": [
			{
				"name": "Get SSO Page",
				"event": [
					{
						"listen": "test",
						"script": {
							"id": "282bdf93-3a98-4066-842e-16e3f21f63b1",
							"exec": [
								"var jsonData = pm.response.json();",
								"pm.environment.set(\"wp_access_token\", jsonData.data);"
							],
							"type": "text/javascript"
						}
					}
				],
				"request": {
					"method": "GET",
					"header": [],
					"url": {
						"raw": "{{url_sso}}/oauth/login?client_id=1&redirect_uri=https://intools-staging.warungpintar.co/callback&response_type=code&state=xyz",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"login"
						],
						"query": [
							{
								"key": "client_id",
								"value": "1"
							},
							{
								"key": "redirect_uri",
								"value": "https://intools-staging.warungpintar.co/callback"
							},
							{
								"key": "response_type",
								"value": "code"
							},
							{
								"key": "state",
								"value": "xyz"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Token",
				"event": [
					{
						"listen": "test",
						"script": {
							"id": "282bdf93-3a98-4066-842e-16e3f21f63b1",
							"exec": [
								"var jsonData = pm.response.json();",
								"pm.environment.set(\"wp_access_token\", jsonData.data);"
							],
							"type": "text/javascript"
						}
					}
				],
				"request": {
					"method": "GET",
					"header": [],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/accesstoken?user_id=186&apps_id=1&email=rezahidayat@warungpintar.co&name=reza",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"accesstoken"
						],
						"query": [
							{
								"key": "user_id",
								"value": "186"
							},
							{
								"key": "apps_id",
								"value": "1"
							},
							{
								"key": "email",
								"value": "rezahidayat@warungpintar.co"
							},
							{
								"key": "name",
								"value": "reza"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Access Request Status",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/accessrequest/status?trx_id=23",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"accessrequest",
							"status"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "23"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Find Access Request",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"value": "Bearer {{wp_access_token}}",
							"type": "text"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/accessrequest?order_by=id asc&per_page=10&page=1&trx_id=asd&name=isti&status_id=1",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"accessrequest"
						],
						"query": [
							{
								"key": "order_by",
								"value": "id asc"
							},
							{
								"key": "per_page",
								"value": "10"
							},
							{
								"key": "page",
								"value": "1"
							},
							{
								"key": "trx_id",
								"value": "asd"
							},
							{
								"key": "name",
								"value": "isti"
							},
							{
								"key": "status_id",
								"value": "1"
							},
							{
								"key": "email",
								"value": "ajeng",
								"disabled": true
							},
							{
								"key": "role_id",
								"value": "2",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Create Access Request",
				"request": {
					"method": "POST",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json",
							"disabled": true
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\":\"a53029f0-fedf-11e9-bfda-753b72dcb1d1\",\n\t    \"email\" : \"rezahidayat@warungpintar.co\",\n\t    \"role_id\" : 1,\n\t    \"remarks\" : \"test aja2xx\"\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/accessrequest",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"accessrequest"
						]
					}
				},
				"response": []
			},
			{
				"name": "Update Access Request",
				"request": {
					"method": "PUT",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\":\"111\",\n\t    \"id\" : 35,\n\t    \"status\" : 1\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/accessrequest",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"accessrequest"
						]
					}
				},
				"response": []
			},
			{
				"name": "Get all Role",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"type": "text",
							"value": "application/json",
							"disabled": true
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/roles?trx_id=123&all=true",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"roles"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "123",
								"description": "wajib"
							},
							{
								"key": "all",
								"value": "true",
								"description": "wajib diisi true"
							},
							{
								"key": "order_by",
								"value": "id ASC",
								"description": "optional",
								"disabled": true
							},
							{
								"key": "name",
								"value": "admin",
								"description": "optional",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Paginated Role",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/roles?trx_id=asd&page=1&per_page=10",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"roles"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "asd",
								"description": "mandatory"
							},
							{
								"key": "page",
								"value": "1",
								"description": "mandatory"
							},
							{
								"key": "per_page",
								"value": "10",
								"description": "mandatory"
							},
							{
								"key": "order_by",
								"value": "id ASC",
								"description": "optional",
								"disabled": true
							},
							{
								"key": "name",
								"value": "Ops",
								"description": "optional",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Create Role",
				"request": {
					"method": "POST",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\t\"trx_id\":\"444\",\n\t\t\t\"name\":\"AdminVoucher\"\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/roles",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"roles"
						]
					}
				},
				"response": []
			},
			{
				"name": "Update Role",
				"request": {
					"method": "PUT",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\t\"trx_id\":\"444\",\n\t\t\t\"id\" : 81,\n\t\t\t\"name\":\"Testing\"\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/roles",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"roles"
						]
					}
				},
				"response": []
			},
			{
				"name": "Delete Role",
				"request": {
					"method": "DELETE",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\t\"trx_id\":\"444\",\n\t\t\t\"id\" : 68\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/roles",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"roles"
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Assigned Permission by RoleID",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"type": "text",
							"value": "application/json",
							"disabled": true
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/role-permission?trx_id=123&role_id=1",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"role-permission"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "123"
							},
							{
								"key": "role_id",
								"value": "1"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Update Assigned Permission by RoleID",
				"request": {
					"method": "PUT",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\":\"444\",\n\t\t\"role_id\":62,\n\t\t\"permission_access\":[\n\t\t\t{\n\t\t\t\t\"permission_id\" : 4,\n\t\t\t\t\"access_level\": 3\n\t\t\t},\n\t\t\t{\n\t\t\t\t\"permission_id\" : 2,\n\t\t\t\t\"access_level\": 3\n\t\t\t},\n\t\t\t{\n\t\t\t\t\"permission_id\" : 3,\n\t\t\t\t\"access_level\": 3\n\t\t\t}\n\t\t]\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/role-permission",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"role-permission"
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Paginated Permission Role by RoleID",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"type": "text",
							"value": "application/json",
							"disabled": true
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/role-permission?trx_id=123&list=true&list_type=role&per_page=4&page=2&role_id=1&order_by=id ASC",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"role-permission"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "123",
								"description": "wajib"
							},
							{
								"key": "list",
								"value": "true",
								"description": "wajib di isi true"
							},
							{
								"key": "list_type",
								"value": "role",
								"description": "wajib di isi role"
							},
							{
								"key": "per_page",
								"value": "4",
								"description": "wajib"
							},
							{
								"key": "page",
								"value": "2",
								"description": "wajib"
							},
							{
								"key": "role_id",
								"value": "1",
								"description": "wajib"
							},
							{
								"key": "order_by",
								"value": "id ASC",
								"description": "optional"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Paginated Permission Role by PermissionID",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"type": "text",
							"value": "application/json",
							"disabled": true
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/role-permission?trx_id=123&list=true&list_type=permission&per_page=4&page=2&permission_id=2&order_by=id DESC",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"role-permission"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "123",
								"description": "wajib"
							},
							{
								"key": "list",
								"value": "true",
								"description": "wajib diisi true"
							},
							{
								"key": "list_type",
								"value": "permission",
								"description": "wajib diisi permission"
							},
							{
								"key": "per_page",
								"value": "4",
								"description": "wajib"
							},
							{
								"key": "page",
								"value": "2",
								"description": "wajib"
							},
							{
								"key": "permission_id",
								"value": "2",
								"description": "wajib"
							},
							{
								"key": "order_by",
								"value": "id DESC",
								"description": "optional"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get all Permission",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"type": "text",
							"value": "application/json",
							"disabled": true
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/permissions?trx_id=123&all=true",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"permissions"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "123",
								"description": "wajib"
							},
							{
								"key": "all",
								"value": "true",
								"description": "wajib diisi true"
							},
							{
								"key": "order_by",
								"value": "id ASC",
								"description": "optional",
								"disabled": true
							},
							{
								"key": "resources",
								"value": "user",
								"description": "optional",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get paginated Permission",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/permissions?trx_id=asd&per_page=10&page=1&resources=user&order_by=id DESC",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"permissions"
						],
						"query": [
							{
								"key": "trx_id",
								"value": "asd",
								"description": "mandatory"
							},
							{
								"key": "per_page",
								"value": "10",
								"description": "mandatory"
							},
							{
								"key": "page",
								"value": "1",
								"description": "mandatory"
							},
							{
								"key": "resources",
								"value": "user",
								"description": "optional"
							},
							{
								"key": "order_by",
								"value": "id DESC",
								"description": "optional"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Create Permission",
				"request": {
					"method": "POST",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\":\"444\",\n\t\t\"resources\":\"Test\",\n\t\t\"service_name\":\"point\",\n\t\t\"apps_id\":1\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/permissions",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"permissions"
						]
					}
				},
				"response": []
			},
			{
				"name": "Update Permission",
				"request": {
					"method": "PUT",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\":\"444\",\n\t\t\"id\":20,\n\t\t\"resources\":\"Test\",\n\t\t\"service_name\":\"pointt\",\n\t\t\"apps_id\":1\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/permissions",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"permissions"
						]
					}
				},
				"response": []
			},
			{
				"name": "DeletePermission",
				"request": {
					"method": "DELETE",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\":\"444\",\n\t\t\"id\":20\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/permissions",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"permissions"
						]
					}
				},
				"response": []
			},
			{
				"name": "Create Activity",
				"request": {
					"method": "POST",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"trx_id\":\"123\",\n\t\"data\":{\n\t\t\"user_id\":119,\n\t\t\"resources\":\"test\",\n\t\t\"description\":\"Test description\"\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/activity",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"activity"
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Activities",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/activity?order_by=id asc&per_page=10&page=1&trx_id=123123123&filter_resources=access",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"activity"
						],
						"query": [
							{
								"key": "order_by",
								"value": "id asc"
							},
							{
								"key": "per_page",
								"value": "10"
							},
							{
								"key": "page",
								"value": "1"
							},
							{
								"key": "trx_id",
								"value": "123123123"
							},
							{
								"key": "filter_resources",
								"value": "access"
							},
							{
								"key": "filter_trx_id",
								"value": "",
								"disabled": true
							},
							{
								"key": "filter_user_id",
								"value": "ajeng",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Access Level",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/accesslevel?order_by=id asc&per_page=10&page=1&trx_id=123123123",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"accesslevel"
						],
						"query": [
							{
								"key": "order_by",
								"value": "id asc"
							},
							{
								"key": "per_page",
								"value": "10"
							},
							{
								"key": "page",
								"value": "1"
							},
							{
								"key": "trx_id",
								"value": "123123123"
							},
							{
								"key": "name",
								"value": "ajeng",
								"disabled": true
							},
							{
								"key": "status_id",
								"value": "1",
								"disabled": true
							},
							{
								"key": "email",
								"value": "ajeng",
								"disabled": true
							},
							{
								"key": "role_id",
								"value": "2",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Access Level Copy",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/apps?order_by=id asc&per_page=10&page=1&trx_id=123123123&name=cms",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"apps"
						],
						"query": [
							{
								"key": "order_by",
								"value": "id asc"
							},
							{
								"key": "per_page",
								"value": "10"
							},
							{
								"key": "page",
								"value": "1"
							},
							{
								"key": "trx_id",
								"value": "123123123"
							},
							{
								"key": "name",
								"value": "cms"
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Create Apps",
				"request": {
					"method": "POST",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"type": "text",
							"value": "application/json"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\": \"111\",\n\t\t\"name\":\"CMS 2\",\n\t\t\"redirect_uri\":\"http://localhost/callback\"\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/apps",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"apps"
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Users",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/users?order_by=id asc&per_page=10&page=1&trx_id=123123123&id=46&status_id=1",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"users"
						],
						"query": [
							{
								"key": "order_by",
								"value": "id asc"
							},
							{
								"key": "per_page",
								"value": "10"
							},
							{
								"key": "page",
								"value": "1"
							},
							{
								"key": "trx_id",
								"value": "123123123"
							},
							{
								"key": "id",
								"value": "46"
							},
							{
								"key": "name",
								"value": "ajeng",
								"disabled": true
							},
							{
								"key": "email",
								"value": "ajengt@",
								"disabled": true
							},
							{
								"key": "status_id",
								"value": "1"
							},
							{
								"key": "role_id",
								"value": "62",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Update User Status",
				"request": {
					"method": "PUT",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						},
						{
							"key": "Content-Type",
							"name": "Content-Type",
							"value": "application/json",
							"type": "text"
						}
					],
					"body": {
						"mode": "raw",
						"raw": "{\n\t\"data\":{\n\t\t\"trx_id\":\"111\",\n\t    \"id\" : 186,\n\t    \"status\" : 1,\n\t    \"roles\": [\"1\",\"62\"]\n\t}\n}"
					},
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/users",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"users"
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Role By User ID",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/users/119/roles?order_by=id asc&per_page=10&page=1&trx_id=123123123",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"users",
							"119",
							"roles"
						],
						"query": [
							{
								"key": "order_by",
								"value": "id asc"
							},
							{
								"key": "per_page",
								"value": "10"
							},
							{
								"key": "page",
								"value": "1"
							},
							{
								"key": "trx_id",
								"value": "123123123"
							},
							{
								"key": "name",
								"value": "ajeng",
								"disabled": true
							},
							{
								"key": "status_id",
								"value": "1",
								"disabled": true
							},
							{
								"key": "role_id",
								"value": "62",
								"disabled": true
							}
						]
					}
				},
				"response": []
			},
			{
				"name": "Get Permissions By User ID",
				"request": {
					"method": "GET",
					"header": [
						{
							"key": "Authorization",
							"type": "text",
							"value": "Bearer {{wp_access_token}}"
						}
					],
					"url": {
						"raw": "{{url_sso}}/oauth/api/v1/users/119/permissions?order_by=id asc&per_page=10&page=1&trx_id=123123123",
						"host": [
							"{{url_sso}}"
						],
						"path": [
							"oauth",
							"api",
							"v1",
							"users",
							"119",
							"permissions"
						],
						"query": [
							{
								"key": "order_by",
								"value": "id asc"
							},
							{
								"key": "per_page",
								"value": "10"
							},
							{
								"key": "page",
								"value": "1"
							},
							{
								"key": "trx_id",
								"value": "123123123"
							},
							{
								"key": "id",
								"value": "1",
								"disabled": true
							},
							{
								"key": "access_level",
								"value": "4",
								"disabled": true
							},
							{
								"key": "resources",
								"value": "user",
								"disabled": true
							},
							{
								"key": "service_name",
								"value": "point",
								"disabled": true
							},
							{
								"key": "apps_id",
								"value": "",
								"disabled": true
							}
						]
					}
				},
				"response": []
			}
		],
		"protocolProfileBehavior": {}
	}