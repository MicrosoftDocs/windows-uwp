---
description: "Learn more about: Runtime Directive Policy Settings"
title: "Runtime Directive Policy Settings"
ms.date: "03/30/2017"
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
---
# Runtime Directive Policy Settings

Runtime directive policy settings for .NET Native determine the availability of metadata for types and type members at run time. Without the necessary metadata, operations that rely on reflection, serialization and deserialization, or marshaling of .NET Framework types to COM or the Windows Runtime can fail and throw an exception. Most common exceptions are [MissingMetadataException](missingmetadataexception-class-net-native.md) and (in the case of interop) [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Runtime policy settings are controlled by a runtime directives (.rd.xml) file. Each runtime directive defines policy for a particular program element, such as an assembly (the [\<Assembly>](assembly-element-net-native.md) element), a type (the [\<Type>](type-element-net-native.md) element), or a method (the [\<Method>](method-element-net-native.md) element). The directive includes one or more attributes that define the reflection policy types, the serialization policy types, and the interop policy types discussed in the next section. The value of the attribute defines the policy setting.

## Policy types

Runtime directives files recognize three categories of policy types: reflection, serialization, and interop.

- Reflection policy types determine which metadata is made available at run time for reflection:

  - `Activate` controls runtime access to constructors, to enable activation of instances.

  - `Browse` controls querying for information about program elements.

  - `Dynamic` controls runtime access to all types and members to enable dynamic programming.

  The following table lists the reflection policy types and the program elements with which they can be used.

  | Element                                                             | Activate | Browse | Dynamic |
  |---------------------------------------------------------------------|----------|--------|---------|
  | [\<Application>](application-element-net-native.md)                 | ✔️      | ✔️     | ✔️     |
  | [\<Assembly>](assembly-element-net-native.md)                       | ✔️      | ✔️     | ✔️     |
  | [\<AttributeImplies>](attributeimplies-element-net-native.md)       | ✔️      | ✔️     | ✔️     |
  | [\<Event>](event-element-net-native.md)                             |          | ✔️    | ✔️      |
  | [\<Field>](field-element-net-native.md)                             |          | ✔️    | ✔️      |
  | [\<GenericParameter>](genericparameter-element-net-native.md)       | ✔️      | ✔️     | ✔️     |
  | [\<ImpliesType>](impliestype-element-net-native.md)                 | ✔️      | ✔️     | ✔️     |
  | [\<Method>](method-element-net-native.md)                           |          | ✔️    | ✔️      |
  | [\<MethodInstantiation>](methodinstantiation-element-net-native.md) |          | ✔️    | ✔️      |
  | [\<Namespace>](namespace-element-net-native.md)                     | ✔️      | ✔️     | ✔️     |
  | [\<Parameter>](parameter-element-net-native.md)                     | ✔️      | ✔️     | ✔️     |
  | [\<Property>](property-element-net-native.md)                       |          | ✔️    | ✔️      |
  | [\<Subtypes>](subtypes-element-net-native.md)                       | ✔️      | ✔️     | ✔️     |
  | [\<Type>](type-element-net-native.md)                               | ✔️      | ✔️     | ✔️     |
  | [\<TypeInstantiation>](typeinstantiation-element-net-native.md)     | ✔️      | ✔️     | ✔️     |
  | [\<TypeParameter>](typeparameter-element-net-native.md)             | ✔️      | ✔️     | ✔️     |

- Serialization policy types determine which metadata is made available at run time for serialization and deserialization:

  - `Serialize` controls runtime access to constructors, fields, and properties, to enable type instances to be serialized by third-party libraries such as the Newtonsoft JSON serializer.

  - `DataContractSerializer` controls runtime access to constructors, fields, and properties, to enable type instances to be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> class.

  - `DataContractJsonSerializer` controls runtime access to constructors, fields, and properties, to enable type instances to be serialized by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class.

  - `XmlSerializer` controls runtime access to constructors, fields, and properties, to enable type instances to be serialized by the <xref:System.Xml.Serialization.XmlSerializer> class.

  The following table lists the serialization policy types and the program elements with which they can be used.

  |Element|Serialize|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)|||||
  |[\<Field>](field-element-net-native.md)|✔️||||
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)|||||
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)|✔️||||
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|✔️|

- Interop policy types determine which metadata is made available at run time to pass references types, value types, and function pointers to COM and the Windows Runtime:

  - `MarshalObject` controls native marshaling to COM and the Windows Runtime for reference types.

  - `MarshalDelegate` controls native marshaling of delegate types as function pointers.

  - `MarshalStructure` controls native marshaling to COM and the Windows Runtime for value types.

  The following table lists the interop policy types and the program elements with which they can be used.

  | Element                                                             | MarshalObject | MarshalDelegate | MarshalStructure |
  |---------------------------------------------------------------------|---------------|-----------------|------------------|
  | [\<Application>](application-element-net-native.md)                 | ✔️           | ✔️              | ✔️              |
  | [\<Assembly>](assembly-element-net-native.md)                       | ✔️           | ✔️              | ✔️              |
  | [\<AttributeImplies>](attributeimplies-element-net-native.md)       | ✔️           | ✔️              | ✔️              |
  | [\<Event>](event-element-net-native.md)                             |               |                 |                  |
  | [\<Field>](field-element-net-native.md)                             |               |                 |                  |
  | [\<GenericParameter>](genericparameter-element-net-native.md)       | ✔️           | ✔️              | ✔️              |
  | [\<ImpliesType>](impliestype-element-net-native.md)                 | ✔️           | ✔️              | ✔️              |
  | [\<Method>](method-element-net-native.md)                           |               |                 |                  |
  | [\<MethodInstantiation>](methodinstantiation-element-net-native.md) |               |                 |                  |
  | [\<Namespace>](namespace-element-net-native.md)                     | ✔️           | ✔️              | ✔️              |
  | [\<Parameter>](parameter-element-net-native.md)                     | ✔️           | ✔️              | ✔️              |
  | [\<Property>](property-element-net-native.md)                       |               |                 |                  |
  | [\<Subtypes>](subtypes-element-net-native.md)                       | ✔️           | ✔️              | ✔️              |
  | [\<Type>](type-element-net-native.md)                               | ✔️           | ✔️              | ✔️              |
  | [\<TypeInstantiation>](typeinstantiation-element-net-native.md)     | ✔️           | ✔️              | ✔️              |
  | [\<TypeParameter>](typeparameter-element-net-native.md)             | ✔️           | ✔️              | ✔️              |

## Policy settings

Each policy type can be set to one of the values listed in the following table. Note that elements that represent type members support a different set of policy settings than other elements.

|Policy setting|Description|`Assembly`, `Namespace`, `Type`, and `TypeInstantiation` elements|`Event`, `Field`, `Method`, `MethodInstantiation`, and `Property` elements|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|Enables the policy for all types and members that the .NET Native tool chain doesn't remove.|✔️||
|`Auto`|Specifies that the default policy should be used for the policy type for that program element. This is identical to omitting a policy for that policy type. `Auto` is typically used to indicate that policy is inherited from a parent element.|✔️|✔️|
|`Excluded`|Specifies that the policy is disabled for a particular program element. For example, the runtime directive:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> specifies that metadata for the `BusinessClasses.Person` class isn't available either to browse or to dynamically instantiate and modify `Person` objects.|✔️|✔️|
|`Included`|Enables a policy if metadata for the parent type is available.||✔️|
|`Public`|Enables the policy for public types or members, unless the tool chain determines that the type or member is unnecessary and therefore removes it. This setting differs from `Required Public`, which ensures that metadata for public types and members is always available even if the tool chain determines that it's unnecessary.|✔️||
|`PublicAndInternal`|Enables the policy for public and internal types or members, unless the tool chain determines that the type or member is unnecessary and therefore removes it. This setting differs from `Required PublicAndInternal`, which ensures that metadata for public and internal types and members is always available even if the tool chain determines that it's unnecessary.|✔️||
|`Required`|Specifies that the policy for a member is enabled and that metadata will be available even if the member appears to be used.||✔️|
|`Required Public`|Enables the policy for public types or members, and ensures that metadata for public types and members is always available. This setting differs from `Public`, which makes metadata for public types and members available only if the tool chain determines that it's necessary.|✔️||
|`Required PublicAndInternal`|Enables the policy for public and internal types or members, and ensures that metadata for public and internal types and members is always available. This setting differs from `PublicAndInternal`, which makes metadata for public and internal types and members available only if the tool chain determines that it's necessary.|✔️||
|`Required All`|Requires the tool chain to keep all types and members whether or not they're used, and enables policy for them.|✔️||

## See also

- [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md)
- [Runtime Directive Elements](runtime-directive-elements.md)
