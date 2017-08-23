<template>
    <div>
        <Table border stripe :columns="columns7" :data="tabledata1"></Table>
        <div style="margin: 10px;overflow: hidden">
            <div style="float: right;">
                <Page :total="total" :current="1" @on-change="changePage"></Page>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                tabledata1: this.mockTableData1(1),
                total: 12,
                columns7: [
                    {
                        title: '姓名',
                        key: 'name',
                        render: (h, params) => {
                            return h('div', [
                                h('Icon', {
                                    props: {
                                        type: 'person'
                                    }
                                }),
                                h('strong', params.row.name)
                            ]);
                        }
                    },
                    {
                        title: '年龄',
                        key: 'age'
                    },
                    {
                        title: '地址',
                        key: 'address'
                    },
                    {
                        title: '操作',
                        key: 'action',
                        width: 150,
                        align: 'center',
                        render: (h, params) => {
                            return h('div', [
                                h('Button', {
                                    props: {
                                        type: 'primary',
                                        size: 'small'
                                    },
                                    style: {
                                        marginRight: '5px'
                                    },
                                    on: {
                                        click: () => {
                                            this.show(params.index)
                                        }
                                    }
                                }, '查看')
                            ]);
                        }
                    }
                ]
            }
        },
        methods: {
            mockTableData1 (val) {
                let data = [];
                let url = "../../../static/data/data.json";
                this.axios.get(url).then(function(response){
                    for (var i = 0; i < 10; i++) {
                        let tmp = (val - 1) * 10 + i;
                        if (tmp >= response.data.result.length) {
                            break;
                        }
                    data.push(response.data.result[tmp]);
                    }
                });
                return data;
            },
            show (index) {
                this.$Modal.info({
                    title: '用户信息',
                    content: `姓名：${this.tabledata1[index].name}<br>年龄：${this.tabledata1[index].age}<br>地址：${this.tabledata1[index].address}`
                })
            },
            changePage (val) {
                // 这里直接更改了模拟的数据，真实使用场景应该从服务端获取数据
                this.tabledata1 = this.mockTableData1(val);
            }
        },
    }
</script>