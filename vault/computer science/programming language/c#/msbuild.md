- [reference 1](https://www.youtube.com/watch?v=B2nvNMW3LVQ)
- [reference 2](https://www.youtube.com/watch?v=5HEbsyU5E1g)
- [official reference](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-concepts?view=vs-2022)
an xml file, named `*.*proj` that contains a `<Project>` element

```
<Project>

</Project>
```

# method
a method in prog language is equivalent to `<Target>` in msbuild

```
<Project>
	<Target>
	
	<Target>
</Project>
```

# statement
an statement in prog language is equivalent to a Task in msbuild

```
<Project>
	<Target>
		<Message Text="Hello world!" Importance="high"/>
	<Target>
</Project>
```

the project file above prints "Hello world!" to the console

# variable
a variable in prog language is equivalent to a Property in msbuild

```
<Project>
	<PropertyGroup>
		<Greeting>Hello world!</Greeting>
	</PropertyGroup>

	<Target>
		<Message Text="$(Greeting)" Importance="high"/>
	<Target>
</Project>
```

the project file above also prints "Hello world!" to the console

# collection
a collection in prog lang is equivalent to Item in msbuild

```
<Project>
	<ItemGroup>
		<Person Include="John;Michael" />
		<Person Include="Jennyfer" />
	</ItemGroup>

	<Target>
		<Message Text="Hi, @(Person)" Importance="high"/>
	<Target>
</Project>
```

it's possible to **Include**, **Update** and **Remove** an `Item` from `ItemGroup`

the project file above will print:
```
Hi, John;Michael;Jennyfer
```

with Transformation it's possible to iterate through items

```
<Project>
	<ItemGroup>
		<Person Include="John;Michael" />
		<Person Include="Jennyfer" />
	</ItemGroup>

	<Target>
		<Message Text="@(Person->'Hi, %(Identity)')" Importance="high"/>
	<Target>
</Project>
```

the project file above will print three lines
```
Hi, John;Hi, Michael;Hi, Jennyfer
```

# object's property

an object's property in prog lang is equal to Metadata in msbuild

```
<Project>
	<ItemDefinitionGroup>
		<Person>
			<Greeting>Hi, %(Identity)</Greeting>
		</Person>
	</ItemDefinitionGroup>

	<ItemGroup>
		<Person Include="John;Michael" />
		<Person Include="Jennyfer" Greeting="Hi, cute!"/>
	</ItemGroup>

	<Target>
		<Message Text="%(Person.Greeting)" Importance="high"/>
	<Target>
</Project>
```

the project file above will print three lines
```
Hi, John;Hi, Michael;Hi, cute!
```

# item and files

the most useful way to use item is combining it with files

```
<Project>
	<ItemGroup>
		<SomeFile Include="*.ext">
	</ItemGroup>

	<Target>
		
	<Target>
</Project>
```

this project file above will generate a list of files ending in .ext
# control flow
a control flow in prog lang is equivalent to a Condition in msbuild

```
<Project>
	<PropertyGroup>
		<Greeting>Hello world!</Greeting>
	</PropertyGroup>

	<Target Condition="'$(Greeting)' != ''">
		<Message Text="$(Greeting)" Importance="high"/>
	<Target>

	<Target Condition="'$(Greeting)' == ''">
		<Message Text="Hello world!" Importance="high"/>
	<Target>
</Project>
```

# target structure

- targets can declare a name
- the project can declare which target to run by choosing a name

```
<Project DefaultTargets="Target1">
	<Target Name="Target1"></Target>
	<Target Name="Target2"></Target>
</Project>
```

- targets can declare dependency on other targets
- the dependency executes first
- in the example above, Target2 will run first

```
<Project DefaultTargets="Target1">
	<Target Name="Target1" DependsOnTargets="Target2"></Target>
	<Target Name="Target2"></Target>
</Project>
```

>msbuild builds a graph of targets based on dependencies and only executes a target once if it appears twice or more times

- targets can call other targets
- the called target executes later
- in the example above, Target2 will run later

```
<Project DefaultTargets="Target1">
	<Target Name="Target1">
		<CallTarget Targets="Target2" />
	</Target>
	<Target Name="Target2"></Target>
</Project>
```

# import
it's possible to write multiple project files and concatenate them together using `<Import>`
# Directory.Build.*
you can add the files below in a parent directory to create global properties and global targets that are used by all project files
- Directory.Build.props
- Directory.Build.targets

a cool thing that you could do is add to Directory.Build.targets

```
<ItemGroup>
	<PackageReference Update="SomeDependency" Version="GlobalVersion">
</ItemGroup>
```

to save some lines of code by defining a version property with global scope for some package references that are used on multiple projects