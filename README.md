# MultipleTargetWithPods
using cocoapods with multiple targets

* if all targets share the same pod, use "link_with" in Podfile to make pod linked with all targets
<pre>
	link_with 'project_01', 'project_02'
	pod 'nameOfPod'
</pre>

* PODS_ROOT will be genereated in User-Defined field at the bottom of Build Settings at the first target

	![${SRCROOT}/Pods in "User-Defined" section](http://i.stack.imgur.com/Go85Z.png)

	[${SRCROOT}/Pods in "User-Defined" section.](http://stackoverflow.com/a/23852613/1083128)

* if parts of targets use perticular pod, define a pod set, as following

<pre>
	def sharing_pods
		pod 'shareingOne'
		pod 'sharingTwo'
	end
	
	target 'project_01' do
		pod 'podsForOne'
	end
	
	target 'project_02' do
		pod 'podsForTwo'
	end
</pre>

 [CocoaPods: The Elegant Solution To Installing The Same Pod In Multiple Targets](https://www.natashatherobot.com/cocoapods-installing-same-pod-multiple-targets/)
