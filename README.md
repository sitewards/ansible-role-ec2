Creates an instances, and tags the resources created with the approriate cost targets

 See http://docs.ansible.com/ansible/ec2_tag_module.html#examples
 See http://docs.ansible.com/ansible/ec2_remote_facts_module.html
 See https://github.com/ansible/ansible/issues/14593

 This works in three stages:
   1. Idempotently create the instance with a unique ID. If the instance has been created previously, this should fail
      and terminate the run.
   2. Get the ID from that creation. Do no state modification (such as tagging, or stopping and starting) here - the
      implementation is buggy; we may stop or delete the wrong machine.
   3. Modify state based on the fetched ID.
