----- bfs2pack by Karok, release 1.2 ------

- GUI Mode -

-- Unpacks new bfs archives from flatout2 --

1. copy the content of this archive to some directory
2. start bfs2pack_gui.exe
3. drag and drop any bfs archive onto the bfs2pack window
4. choose a directory, where extracted files should be placed

-- Packs files into an bfs archive --

1. copy the content of this archive to some directory
2. start bfs2pack_gui.exe
3. drag and drop a directory onto the bfs2pack window (should contain the same structure like the flatout2-data-dir)
4. choose a filename (.bfs is added automatically)

5. edit file: filesystem, change it, so it looks like:
fo2a.bfs
fo2b.bfs
fo2c.bfs
<YOURNEWBFSHERE>.bfs
6. Notice: There MUST NOT be an empty last line!
7. Start flatout2, have fun!

- Console Mode -

Use bfs2pack_con.exe --help for some help. It basically works like any other archiver program (zip, tar, ...).

-- Note --

Every file is overwritten, WITHOUT any remark! 
