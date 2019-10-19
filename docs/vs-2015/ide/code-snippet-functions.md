---
title: Funkce fragmentu kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 92533b90e6a2da9f29a67d13c6e0eee2c31dbcfe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620240"
---
# <a name="code-snippet-functions"></a>Funkce fragmentu kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existují tři funkce, které lze použít s [!INCLUDE[csprcs](../includes/csprcs-md.md)] fragmenty kódu. Funkce jsou zadány v prvku [funkce](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) fragmentu kódu. Informace o vytváření fragmentů kódu naleznete v tématu [fragmenty kódu](../ide/code-snippets.md).

## <a name="functions"></a>Funkce
 Následující tabulka popisuje funkce, které jsou k dispozici pro použití s elementem `Function` v části fragmenty kódu.

|Funkce|Popis|Jazyk|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Vygeneruje příkaz switch a sadu příkazů Case pro členy výčtu určené parametrem `EnumerationLiteral`. Parametr `EnumerationLiteral` musí být buď odkaz na literál výčtu, nebo typ výčtu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`ClassName()`|Vrátí název třídy, která obsahuje vložený fragment kódu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`SimpleTypeName(` `TypeName` `)`|Zmenší parametr *TypeName* na jeho nejjednodušší tvar v kontextu, ve kterém byl vyvolán fragment kódu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít funkci `GenerateSwitchCases`. Po vložení tohoto fragmentu kódu a zadáním výčtu do `$switch_on$` literálu `$cases$` literál generuje příkaz `case` pro každou hodnotu ve výčtu.

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít funkci `ClassName`. Po vložení tohoto fragmentu je `$classname$` literál nahrazen názvem ohraničující třídy v tomto umístění v souboru kódu.

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="vjsharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak použít funkci `SimpleTypeName`. Když je tento fragment kódu vložen do souboru kódu, bude `$SystemConsole$` literál nahrazen nejjednodušším tvarem <xref:System.Console> typu v kontextu, ve kterém byl fragment vyvolán.

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Viz také
 [Element Function (fragmenty kódu technologie IntelliSense)](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) [reference schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
