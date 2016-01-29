---
title: Simple way to find locked rows
author: Tim
layout: post
redirect_from: /2003/12/21/simple-way-to-find-locked-rows/
category:  How-To
---
I had an application from another group fail, and lock a DB row that I needed to use. In the investigation, a DBA showed me this code to figure out which rows were locked.

<pre>create table show_locks(id_num number);</p>



<p>
  declare
  1x number;
  begin
    for i in 1..[max_id] loop
      insert into show_locks values(i);
      commit;
      update [original_table] set [id] = i where id = i;
    end loop;
  end;
  </pre>

</p>


<p>
  The <code>update</code> will throw an exception, and the max_id of the <code>show_locks</code> table will contain the id of the locked row.  This statement can be run again by updating the <code>1..[max_id]</code> to be <code>[last_id+1]..[max_id]</code>.
</p>


<p>
  I haven&#8217;t tried it, but I didn&#8217;t want to lose the idea either.
</p>
