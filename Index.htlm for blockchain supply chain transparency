class Block {
  constructor(index, timestamp, data, previousHash = "") {
    this.index = index;
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.hash = this.calculateHash();
  }
  calculateHash() {
    return btoa(
      this.index +
      this.previousHash +
      this.timestamp +
      JSON.stringify(this.data)
    );
  }
}

class Blockchain {
  constructor() {
    this.chain = [this.createGenesisBlock()];
  }
  createGenesisBlock() {
    return new Block(0, new Date().toISOString(), "Genesis Block", "0");
  }
  getLatestBlock() {
    return this.chain[this.chain.length - 1];
  }
  addBlock(newBlock) {
    newBlock.previousHash = this.getLatestBlock().hash;
    newBlock.hash = newBlock.calculateHash();
    this.chain.push(newBlock);
  }
}

const pharmaChain = new Blockchain();

function addMedicine(batchId, medicineName, location, status) {
  const data = {
    batchId,
    medicineName,
    location,
    status,
  };
  const block = new Block(
    pharmaChain.chain.length,
    new Date().toISOString(),
    data,
    pharmaChain.getLatestBlock().hash
  );
  pharmaChain.addBlock(block);
  return pharmaChain.chain;
}
