# weixin1021

function getTxCount(address,network) {
  
  // 根据 network 获取 RPC
  let rpcLink = RPC_MAP[network];
  if (!rpcLink) {
    return "Error: Invalid Network Name";
  }

  // 查询地址的交易数量
  const transactionRequest = {
    jsonrpc: "2.0",
    method: "eth_getTransactionCount",
    params: [address, "latest"],
    id: 1
  };
  const transactionResponse = UrlFetchApp.fetch(rpcLink, {
    method: "POST",
    payload: JSON.stringify(transactionRequest),
    headers: {
      "Content-Type": "application/json"
    }
