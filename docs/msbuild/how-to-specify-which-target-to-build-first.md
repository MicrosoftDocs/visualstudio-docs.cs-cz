---
title: 'How to: Specify Which Target to Build First | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a567ca32a78eb6a78aad3702a68a6e08ed122db8
ms.sourcegitcommit: b04c603ce73b993d042ebdf7f3722cf4fe2ef7f4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74316505"
---
# <a name="how-to-specify-which-target-to-build-first"></a>How to: Specify which target to build first
A project file can contain one or more `Target` elements that define how the project is built. The [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) engine builds the first project it finds, and any dependencies, unless the project file contains a `DefaultTargets` attribute, an `InitialTargets` attribute, or a target is specified at the command line using the **-target** switch.

## <a name="use-the-initialtargets-attribute"></a>Use the InitialTargets attribute
 The `InitialTargets` attribute of the `Project` element specifies a target that will run first, even if targets are specified on the command line or in the `DefaultTargets` attribute.

#### <a name="to-specify-one-initial-target"></a>To specify one initial target

- Specify the default target in the `InitialTargets` attribute of the `Project` element. Příklad:

   `<Project InitialTargets="Clean">`

  You can specify more than one initial target in the `InitialTargets` attribute by listing the targets in order, and using a semicolon to separate each target. The targets in the list will be run sequentially.

#### <a name="to-specify-more-than-one-initial-target"></a>To specify more than one initial target

- List the initial targets, separated by semicolons, in the `InitialTargets` attribute of the `Project` element. For example, to run the `Clean` target and then the `Compile` target, type:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Use the DefaultTargets attribute
 The `DefaultTargets` attribute of the `Project` element specifies which target or targets are built if a target is not specified explicitly on the command line. If targets are specified in both the `InitialTargets` and `DefaultTargets` attributes and no target is specified on the command line, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] runs the targets specified in the `InitialTargets` attribute followed by the targets specified in the `DefaultTargets` attribute.

#### <a name="to-specify-one-default-target"></a>To specify one default target

- Specify the default target in the `DefaultTargets` attribute of the `Project` element. Příklad:

   `<Project DefaultTargets="Compile">`

  You can specify more than one default target in the `DefaultTargets` attribute by listing the targets in order, and using a semicolon to separate each target. The targets in the list will be run sequentially.

#### <a name="to-specify-more-than-one-default-target"></a>To specify more than one default target

- List the default targets, separated by semicolons, in the `DefaultTargets` attribute of the `Project` element. For example, to run the `Clean` target and then the `Compile` target, type:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Use the -target Switch
 If a default target is not defined in the project file, or if you do not want to use that default target, you can use the command line switch **-target** to specify a different target. The target or targets specified with the **-target** switch are run instead of the targets specified by the `DefaultTargets` attribute. Targets specified in the `InitialTargets` attribute always run first.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>To use a target other than the default target first

- Specify the target as the first target using the **-target** command line switch. Příklad:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>To use several targets other than the default targets first

- List the targets, separated by semicolons or commas, using the **-target** command line switch. Příklad:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Viz také:
- [MSBuild](../msbuild/msbuild.md)
- [Cíle](../msbuild/msbuild-targets.md)
- [How to: Clean a build](../msbuild/how-to-clean-a-build.md)
