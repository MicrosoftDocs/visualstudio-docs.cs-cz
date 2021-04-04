---
title: Protokolovací nástroje sestavení | Microsoft Docs
description: Pomocí protokolovacích nástrojů nástroje MSBuild můžete spravovat a upravovat výstup sestavení a zobrazovat zprávy, chyby nebo varování v reakci na konkrétní události sestavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b676fe015f5f513a069ffaf6ae4fac59c1a5fa68
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213898"
---
# <a name="build-loggers"></a>Protokolovací nástroje sestavení

Protokolovací nástroje poskytují způsob, jak přizpůsobit výstup sestavení a zobrazit zprávy, chyby nebo varování v reakci na konkrétní události sestavení. Každý protokolovací nástroj je implementován jako třída .NET, která implementuje <xref:Microsoft.Build.Framework.ILogger> rozhraní, které je definováno v sestavení *Microsoft.Build.Framework.dll* .

Existují dva přístupy, které můžete použít při implementaci protokolovacího nástroje:

- Implementujte <xref:Microsoft.Build.Framework.ILogger> rozhraní přímo.
- Odvodit třídu z pomocné třídy, <xref:Microsoft.Build.Utilities.Logger> , která je definována v sestavení *Microsoft.Build.Utilities.dll* . <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> a poskytuje výchozí implementace některých <xref:Microsoft.Build.Framework.ILogger> členů.

  V tomto tématu se dozvíte, jak napsat jednoduchý protokolovací nástroj, který je odvozen z nástroje <xref:Microsoft.Build.Utilities.Logger> , a zobrazuje zprávy v konzole nástroje v reakci na určité události sestavení.

## <a name="register-for-events"></a>Registrovat pro události

Účelem protokolovacího nástroje je shromáždit informace o průběhu sestavení, když jsou hlášeny modulem sestavení, a pak tyto informace vykázat užitečným způsobem. Všechny protokolovací nástroje musí přepsat <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodu, která je v případě, že protokolovací nástroj registruje události. V tomto příkladu protokolovací nástroj registruje pro <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> události, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet2":::

## <a name="respond-to-events"></a>Reakce na události

Teď, když je protokolovací nástroj zaregistrovaný pro konkrétní události, musí tyto události zpracovávat, když k nim dojde. Pro <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> události a protokolovací nástroj jednoduše zapíše krátkou frázi a název souboru projektu, který je součástí události. Všechny zprávy z protokolovacího nástroje se zapisují do okna konzoly.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet3":::

## <a name="respond-to-logger-verbosity-values"></a>Reakce na hodnoty podrobností protokolovacího nástroje

V některých případech můžete chtít protokolovat pouze informace z události, pokud přepínač MSBuild.exe **-verbose** obsahuje určitou hodnotu. V tomto příkladu <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> obslužná rutina události zaznamená zprávu pouze v případě <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> , že vlastnost, která je nastavena přepínačem **-verbose** , je rovna <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet4":::

## <a name="specify-a-logger"></a>Určení protokolovacího nástroje

Jakmile je protokolovací nástroj zkompilován do sestavení, je nutné sdělit nástroji MSBuild, aby používal tento protokolovací nástroj během sestavení. To se provádí pomocí přepínače **-protokolovacího** nástroje s *MSBuild.exe*. Další informace o přepínačích, které jsou k dispozici pro *MSBuild.exe*, najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

Následující příkazový řádek sestaví projekt *MyProject. csproj* a používá třídu protokolovacího nástroje implementovanou v *SimpleLogger.dll*. Přepínač **-unlogo** skryje hlavičku a zprávu o autorských právech a přepínač **-noconsolelogger** zakáže výchozí protokolovací nástroj konzoly MSBuild.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Následující příkazový řádek sestaví projekt se stejným protokolovacím nástrojem, ale s `Verbosity` úrovní `Detailed` .

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example-1"></a>Příklad 1

### <a name="description"></a>Description

Následující příklad obsahuje úplný kód pro protokolovací nástroj.

### <a name="code"></a>Kód

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet1":::

## <a name="example-2"></a>Příklad 2

### <a name="description"></a>Description

Následující příklad ukazuje, jak implementovat protokolovací nástroj, který zapisuje protokol do souboru namísto zobrazení v okně konzoly.

### <a name="code"></a>Kód

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs" id="Snippet1":::

## <a name="see-also"></a>Viz také

- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
