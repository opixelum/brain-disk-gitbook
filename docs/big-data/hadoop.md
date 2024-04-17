# Hadoop

## HDFS

### Architecture

- 1 file is divided by blocks;
- 128 MB per block;
- NameNode (master): has multiple children (DataNodes);
- DataNode (slave/worker): has only one parent (NameNode) and contains file
  blocks;
- 1 NameNode or DataNode = 1 computer;
- When dividing a file, the NameNode knows where each file block is;
- The file division and recomposition is done outside the architecture (the
  NameNode received file already divided in blocks, and when a use ask for a
  file, it doesn't recompose the file for him, it just gives the file blocks);
- Usual file replication is 3: for 4 file blocks, there will be 12 file blocks
  in total.
  One replication of the same file block per DataNode if possible.
- In the majority of cases, there are 2 NameNodes (1 primary, 1 secondary for
  backing up in case the primary fails);
  DataNodes are linked to the primary NameNode, and there is a symbolic link
  between the two NameNodes.
  The secondary NameNode mirrors the primary one: the primary one shares all
  informations about what it's doing;
- It's ok to have empty DataNodes in case of smaller files.
