## 0.1.0rc0 (2023-11-06)

### Bug Fixes

- **find_id**: [d2d48262](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/d2d4826247289debfa4d073baefc15d8048a5436) - remove empty id from dict [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_search**: [b50a3e91](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/b50a3e9156f3d18dd43fe495c86cca465ccd38c6) - set var tickettemplates_id for ticket template item [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_config**: [00ecd6e0](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/00ecd6e0e30254c2e87f84b1196d534df576cfd9) - typo in Add/Update GLPI Config [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_search**: [93f069c1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/93f069c1b39e882e0a1a341c6352de600b68af17) - typo in tickettemplates_id_demand [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]

### Code Refactor

- **api_config**: [d637f915](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/d637f915c5de32fdd854b9f72f3c1a6eb5ca1d04) - iterate over results [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_config**: [6d7c169b](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/6d7c169bc8cfffbcf094469871316282435a35d8) - move all search by name to own tasks file [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_config**: [b0ce3b00](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/b0ce3b00227c0141e9c9f7cd0b5be40ed7e735ee) - dont log data manipulation [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_config**: [d2902b9a](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/d2902b9ab055cc0b3e599da1f0f4ecb4d9e7b474) - updated flow and docs [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]

### Continious Integration

- **pages**: [024d6c6d](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/024d6c6d6e1f04a2159ff31d3f31e276aa4ad983) - added pages environment path [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]

### Documentaton / Guides

- **issue_1**: [23569ee7](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/23569ee76a53fb4ae0c815bc086d5eac374ff455) - add note about exporting [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **fix**: [b91acddf](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/b91acddf16d420ff8fbc0578a3fdb0c771fc3a64) - wasnt rendering correctly [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]

### Features

- **http_cert_validation**: [33c882f0](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/33c882f005c26e86bd19e5ed4f2ad11ab7f5b0b6) - new option specify cert validation, default true [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **url**: [7c82e3a1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/7c82e3a18d992db25577a8611fa964ae555469a9) - specify url seperate from protocol, defaults to httpt [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [9a820cd1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/9a820cd1a0db9144bc13b859d8dc25a77c19eee5) - search for groups_id by name [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **config**: [40e62997](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/40e629974128b3788cdfadea37e7aa2caae115de) - Add Ticket Template Config from code [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_config**: [baf086de](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/baf086de642513657d4f70dbb497f9e755b7e557) - force an empty list if not config [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api_config**: [910663eb](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/910663eb19fcd61bfa9b7419bcb75b3a4d1be62b) - exlude instance_uuid item from configuration [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **config**: [4407e57f](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/4407e57fdd56dc49be7b7b5e3550069b2ab7eca4) - Add General Settings Config from code [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **config**: [70a48341](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/70a48341a4f1ec510626b0db212a6c6d3fd60826) - Configure GLPI from json config files [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [febce3aa](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/febce3aa5e6bb07ca62aae627a1110acc075038a) - Create and end a session [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [15573f03](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/15573f03cdb37aef2cc8c6fa5df2f9fb868041fc) - end a session [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [e8a5edda](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/e8a5edda5cb2a28366f3aba6bd4313e68f593708) - fetch session id [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [e1d6dba5](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/e1d6dba5ef9de34b90992f04ee1ebae1e93b6f43) - search for users_id by name [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [a0103570](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/a0103570f5d8e6cffee374c32fc1a2c279ae1ed4) - search for itilcategory_id by name [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [825aade1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/825aade159aed773161ff8ca946ce25065359026) - search for tickettemplates_id_demand by name [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [4624f5c8](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/4624f5c80d43c76d1b658c4852507b26a2c1a30d) - search for item_id by name [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **api**: [741107e0](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/741107e0b20f63d98e8044254be4fee2abe81204) - search for entities_id by name [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **docs**: [1c78ec03](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/1c78ec036ccaa2a822c419d9b5b8c0f28cb5b131) - added docs [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **ci**: [62081982](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/62081982e83ed1fbbec2e221ddcfc3df2a849258) - added ci repo [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]
- **migration**: [d1813b93](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/commit/d1813b939183d85fb24c381ed169fa53bf802151) - initial adding of role to repo [ [!1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/merge_requests/1) ]

## 0.0.1 (2023-07-27)
