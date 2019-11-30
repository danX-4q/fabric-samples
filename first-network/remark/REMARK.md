
./byfn.sh generate -c zrchannel -i 1.4.4 -l node
./byfn.sh down -c zrchannel -i 1.4.4 -l node
./byfn.sh up -c zrchannel -i 1.4.4 -l node

./runtcc.sh -c zrchannel
    run scripts/tcc.sh

docker exec -it cli bash
    . utils.sh
    peer channel -c zrchannel fetch 5 > zrchannle_5.block
    configtxlator proto_decode --type=common.Block --input=zrchannel_5.block --output=zrchannel_5.json
        zrchannel_5.block
        zrchannel_5.json

Fabric命令手册
http://cw.hubwiz.com/card/c/fabric-command-manual/

hyperledge工具-configtxlator
https://www.cnblogs.com/wanghui-garcia/p/10497415.html
    合法原型名如下：
    common.Block：区块结构；
    common.Envelope：带有效载荷和数字签名的数字信封，区块的数据部分就是序列化后的数字信封；
    common.ConfigEnvelope：包含链配置的数字信封，内容包含ConfigUpdateEnvelope；
    common.ConfigUpdateEnvelope：提交给排序节点的配置数字信封；
    common.Config：ConfigEnvelope的配置部分；
    common.ConfigUpdate：ConfigUpdateEnvelope的一部分。

fabric/core/rest
    通过tx-uuid查询交易的信息