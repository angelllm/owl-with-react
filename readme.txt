npm config set registry ��https://registry.npm.taobao.org��
��װ
npm install  yo generator-reactpackage -g
//�������ּ�
yo reactpackage

npm run dev
npm run build


//react���
1.import WebHeader from './include/WebHeader';
�����ģ������ ��Ҫ ��д��ͷ

'use strict';


import React from 'react';
import ReactDom from 'react-dom';
import { Router, Route, hashHistory } from 'react-router';

import WebHeader from './include/WebHeader';
import WebMinHeader from './include/WebMinHeader';
import WebFooter from './include/webFooter';

class App extends React.Component {
     
    render() {
        return (
            <div>
                <WebHeader />
                <WebMinHeader />
                <WebFooter />
             </div>
        )
    }
}
 
 
//������Ⱦ
ReactDom.render(<App /> ,document.getElementById('app'));

��Ȼ App��render �������� WebHeader��htmlԪ��

2.�ڻ�ȡmodelʵ���� ��ҳ�����
{this.state.art.article_title}
���ǵ�����
{art.article_title}
�����art 100%��undefined


3.����ģ������
������ ��������ҳ ��ͨID�л�ʱ�� ���ݲ��仯 
��Ϊģ�帴�õĹ�ϵ componentDidMount ֻ��������ص�ʱ�����һ�κ�û�к�����

��ʱ���Ǽ���hashchange�¼� ��ȡurl�ַ�������ѯ�Ϳ��Խ��

    componentDidMount(){
        this.getList()
        var _this = this
        window.addEventListener('hashchange', function(to,from){
            let _urlsplit = to.newURL.split("#")[1]
            if (_urlsplit.indexOf("?_k") !== -1) return
            let _params = _urlsplit.split("?")
            let _url = _params[0].split("/")
            let _id = _url[2]
            _this.getList(_id)

        }, false);
    }


