---
title: Funkce fragmentu kódu
description: Seznamte se s funkcemi GenerateSwitchCases (EnumerationLiteral), ClassName () a SimpleType (TypeName), které jsou k dispozici pro použití s fragmenty kódu v jazyce C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce569dabca9e5d867310b8d510975331f5a9f046
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954433"
---
# <a name="code-snippet-functions"></a>Funkce fragmentu kódu

Existují tři funkce, které lze použít s fragmenty kódu v jazyce C#. Funkce jsou zadány v prvku [funkce](../ide/code-snippets-schema-reference.md#function-element) fragmentu kódu. Informace o vytváření fragmentů kódu naleznete v tématu [fragmenty kódu](../ide/code-snippets.md).

## <a name="functions"></a>Functions

Následující tabulka popisuje funkce, které jsou k dispozici pro použití s `Function` elementem v fragmentech kódu.

|Funkce|Description|Jazyk|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Vygeneruje příkaz switch a sadu příkazů Case pro členy výčtu určené `EnumerationLiteral` parametrem. `EnumerationLiteral`Parametr musí být buď odkaz na literál výčtu, nebo typ výčtu.|C#|
|`ClassName()`|Vrátí název třídy, která obsahuje vložený fragment kódu.|C#|
|`SimpleTypeName(TypeName)`|Zmenší parametr *TypeName* na jeho nejjednodušší tvar v kontextu, ve kterém byl vyvolán fragment kódu.|C#|

## <a name="generateswitchcases-example"></a>Příklad GenerateSwitchCases

Následující příklad ukazuje, jak používat `GenerateSwitchCases` funkci. Po vložení tohoto fragmentu kódu a zadání výčtu do `$switch_on$` literálu je `$cases$` literál vygenerován `case` příkazem pro každou hodnotu ve výčtu.

```xml
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

## <a name="classname-example"></a>Příklad ClassName

Následující příklad ukazuje, jak používat `ClassName` funkci. Po vložení tohoto fragmentu bude `$classname$` literál nahrazen názvem ohraničující třídy v tomto umístění v souboru kódu.

```xml
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
            <Code Language="csharp" Format="CData">
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

## <a name="simpletypename-example"></a>Příklad SimpleType

Tento příklad ukazuje, jak používat `SimpleTypeName` funkci. Když je tento fragment kódu vložen do souboru kódu, `$SystemConsole$` literál bude nahrazen nejjednodušším tvarem <xref:System.Console> typu v kontextu, ve kterém byl vyvolán fragment kódu.

```xml
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

- [Element Function](../ide/code-snippets-schema-reference.md#function-element)
- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
