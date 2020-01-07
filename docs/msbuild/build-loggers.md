---
title: Protokolovací nástroje sestavení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c82b7456e0fc497b753c87f7a4d6808c81d5ab2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593405"
---
# <a name="build-loggers"></a>Protokolovací nástroje sestavení
Protokolovací nástroje poskytují způsob, jak přizpůsobit výstup sestavení a zobrazit zprávy, chyby nebo varování v reakci na konkrétní události sestavení. Každý protokolovací nástroj je implementován jako třída .NET, která implementuje rozhraní <xref:Microsoft.Build.Framework.ILogger>, které je definováno v sestavení *Microsoft. Build. Framework. dll* .

Existují dva přístupy, které můžete použít při implementaci protokolovacího nástroje:

- Implementujte rozhraní <xref:Microsoft.Build.Framework.ILogger> přímo.
- Odvodit třídu z pomocné třídy, <xref:Microsoft.Build.Utilities.Logger>, která je definována v sestavení *Microsoft. Build. Utilities. dll* . <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> a poskytuje výchozí implementace některých <xref:Microsoft.Build.Framework.ILogger> členů.

  V tomto tématu se dozvíte, jak napsat jednoduchý protokolovací nástroj, který je odvozený z <xref:Microsoft.Build.Utilities.Logger>, a zobrazuje zprávy v konzole v reakci na určité události sestavení.

## <a name="register-for-events"></a>Registrovat pro události
Účelem protokolovacího nástroje je shromáždit informace o průběhu sestavení, když jsou hlášeny modulem sestavení, a pak tyto informace vykázat užitečným způsobem. Všechny protokolovací nástroje musí přepsat metodu <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, která je v případě, že protokolovací nástroj registruje události. V tomto příkladu protokolovací nástroj zaregistruje události <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Reakce na události
Teď, když je protokolovací nástroj zaregistrovaný pro konkrétní události, musí tyto události zpracovávat, když k nim dojde. Pro <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>a události <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> protokolovací nástroj jednoduše zapíše krátkou frázi a název souboru projektu, který je součástí události. Všechny zprávy z protokolovacího nástroje se zapisují do okna konzoly.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Reakce na hodnoty podrobností protokolovacího nástroje
V některých případech můžete chtít protokolovat pouze informace z události, pokud přepínač MSBuild. exe **-verbose** obsahuje určitou hodnotu. V tomto příkladu obslužná rutina události <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> zaznamená zprávu pouze v případě, že vlastnost <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, která je nastavena přepínačem **-verbose** , je rovna <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Určení protokolovacího nástroje
Jakmile je protokolovací nástroj zkompilován do sestavení, je nutné sdělit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], aby používal tento protokolovací nástroj během sestavení. To se provádí pomocí přepínače **-protokolovacího** nástroje s nástrojem *MSBuild. exe*. Další informace o přepínačích, které jsou k dispozici pro *MSBuild. exe*, naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

Následující příkazový řádek sestaví projekt *MyProject. csproj* a používá třídu protokolovacího nástroje implementovanou v souboru *SimpleLogger. dll*. Přepínač **-unlogo** skryje hlavičku a zprávu o autorských právech a přepínač **-noconsolelogger** zakáže výchozí protokolovací nástroj konzoly [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Následující příkazový řádek sestaví projekt se stejným protokolovacím nástrojem, ale s úrovní `Verbosity` `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis
Následující příklad obsahuje úplný kód pro protokolovací nástroj.

### <a name="code"></a>Kód
[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis
Následující příklad ukazuje, jak implementovat protokolovací nástroj, který zapisuje protokol do souboru namísto zobrazení v okně konzoly.

### <a name="code"></a>Kód
[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Viz také:
- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
