# 포트원 module 수정

## /Users/youngsup/Desktop/tikkle/node_modules/iamport-react-native/src/components/Payment/index.tsx 파일에 settle_acc를 추가

export const PG = [

'html5_inicis',

'inicis',

'uplus',

'kcp',

'kcp_billing',

'nice',

'jtnet',

'kakao',

'kakaopay',

'danal',

'danal_tpay',

'kicc',

'settle',

'mobilians',

'payco',

'eximbay',

'paypal',

'naverco',

'naverpay',

'smilepay',

'chai',

'payple',

'alipay',

'bluewalnut',

'tosspay',

'smartro',

'tosspayments',

'ksnet',

'daou',

'settle_acc',

] as const;

## /Users/youngsup/Desktop/tikkle/node_modules/iamport-react-native/src/components/Payment/index.tsx 에 settle_acc로 시작하는 로직 추가

const isIframeWayPayment = () => {

const { pg, pay_method, customer_uid } = data;

if (pg.startsWith('html5_inicis') && customer_uid) {

// 이니시스 빌링결제

return true;

}

if (pg.startsWith('mobilians') && pay_method === 'phone') {

// 모빌리언스 휴대폰 소액결제

return true;

}

return (

pg.startsWith('danal') ||

pg.startsWith('danal_tpay') ||

pg.startsWith('smilepay') ||

pg.startsWith('payco') ||

pg.startsWith('bluewalnut') ||

pg.startsWith('settle_acc')

);

};