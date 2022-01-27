# Tips to start a Laravel project

this guide helps you to start a fresh Laravel project and add tools to it for a better developer experience.

### Table of contents:

- [1. Installing requirements](#1-installing-requirements)
- [2. Create a Laravel project](#1-create-a-laravel-project)
- [3. Add dev packages to project](#3-add-dev-packages-to-project)
- [4. Integrate dev tools with git hooks](#4-integrate-dev-tools-with-git-hooks)

### 1. Installing requirements

first install PHP and composer on your host.
you can install PHP on your system based on your OS:

- [PHP installation guide](https://www.php.net/manual/en/install.php)
- [Composer installation guide](https://getcomposer.org/doc/00-intro.md)

###### you can also use WAMP, XAMP, Laragon, etc.

###### if you want to use other features of laravel you should install redis, MySQL on your host too.

### 2. Create a Laravel project

use this command to create a fresh Laravel project:

```bash
$ composer create-project --prefer-dist laravel/laravel MY_AWESOME_LARAVEL_PROJECT_NAME
```

###### use this link for more information: [https://laravel.com/docs/8.x](https://laravel.com/docs/8.x)

### 3. Add dev packages to project

add these packages to your project for better developer experience and enforces every developer to use same coding standard when contributing to your project:

- [PHP CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [PHP CS Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

use these command to add packages:

```bash
composer require --dev friendsofphp/php-cs-fixer
composer require --dev squizlabs/php_codesniffer
```

PHP CodeSniffer uses a configuration file. create a file named `phpcs.xml` and copy this config in it:

```xml
<?xml version="1.0"?>
<ruleset name="Laravel Standards">
    <description>PSR-2 The Laravel conventions</description>
    <rule ref="Generic.Classes.DuplicateClassName">
        <exclude name="Generic.CodeAnalysis.EmptyStatement.DetectedIf"/>
    </rule>
    <rule ref="Generic.CodeAnalysis.EmptyStatement"/>
    <rule ref="Generic.CodeAnalysis.ForLoopShouldBeWhileLoop"/>
    <rule ref="Generic.CodeAnalysis.ForLoopWithTestFunctionCall"/>
    <rule ref="Generic.CodeAnalysis.JumbledIncrementer"/>
    <rule ref="Generic.CodeAnalysis.UnconditionalIfStatement"/>
    <rule ref="Generic.CodeAnalysis.UnnecessaryFinalModifier"/>
    <rule ref="Generic.CodeAnalysis.UnusedFunctionParameter">
        <exclude-pattern>/app/Http/Resources/*\.php</exclude-pattern>
    </rule>
    <rule ref="Generic.CodeAnalysis.UselessOverridingMethod"/>
    <rule ref="Generic.Commenting.DocComment">
        <exclude name="Generic.Commenting.DocComment.TagValueIndent"/>
        <exclude name="Generic.Commenting.DocComment.NonParamGroup"/>
    </rule>
    <rule ref="Generic.ControlStructures.InlineControlStructure"/>
    <rule ref="Generic.Files.ByteOrderMark"/>
    <rule ref="Generic.Files.LineEndings">
        <exclude name="Generic.Files.LineEndings.InvalidEOLChar"/>
    </rule>
    <rule ref="Generic.Formatting.DisallowMultipleStatements"/>
    <rule ref="Generic.Formatting.SpaceAfterCast"/>
    <rule ref="Generic.Functions.CallTimePassByReference"/>
    <rule ref="Generic.Functions.FunctionCallArgumentSpacing"/>
    <rule ref="Generic.Functions.OpeningFunctionBraceBsdAllman"/>
    <rule ref="Generic.Metrics.CyclomaticComplexity">
        <properties>
            <property name="complexity" value="20"/>
            <property name="absoluteComplexity" value="25"/>
        </properties>
    </rule>
    <rule ref="Generic.Metrics.NestingLevel">
        <properties>
            <property name="nestingLevel" value="5"/>
            <property name="absoluteNestingLevel" value="15"/>
        </properties>
    </rule>
    <rule ref="Generic.NamingConventions.ConstructorName"/>
    <rule ref="Generic.PHP.LowerCaseConstant"/>
    <rule ref="Generic.PHP.DeprecatedFunctions"/>
    <rule ref="Generic.PHP.DisallowShortOpenTag"/>
    <rule ref="Generic.PHP.ForbiddenFunctions"/>
    <rule ref="Generic.PHP.NoSilencedErrors"/>
    <rule ref="Generic.WhiteSpace.DisallowTabIndent"/>
    <rule ref="Generic.WhiteSpace.ScopeIndent">
        <properties>
            <property name="indent" value="4"/>
            <property name="tabIndent" value="true"/>
        </properties>
    </rule>
    <rule ref="MySource.PHP.EvalObjectFactory"/>
    <rule ref="PSR1.Classes.ClassDeclaration"/>
    <rule ref="PSR1.Files.SideEffects"/>
    <rule ref="PSR2.Classes.ClassDeclaration"/>
    <rule ref="PSR2.Classes.PropertyDeclaration"/>
    <rule ref="PSR2.ControlStructures.ControlStructureSpacing"/>
    <rule ref="PSR2.ControlStructures.ElseIfDeclaration"/>
    <rule ref="PSR2.ControlStructures.SwitchDeclaration"/>
    <rule ref="PSR2.Files.EndFileNewline"/>
    <rule ref="PSR2.Methods.MethodDeclaration"/>
    <rule ref="PSR2.Namespaces.NamespaceDeclaration"/>
    <rule ref="PSR2.Namespaces.UseDeclaration"/>
    <rule ref="PSR1">
        <exclude-pattern>*.php</exclude-pattern>
        <exclude name="PSR1.Methods.CamelCapsMethodName.NotCamelCaps"/>

        <exclude-pattern>database/*</exclude-pattern>
    </rule>
    <rule ref="PSR2">
        <exclude name="PSR2.ControlStructures.SwitchDeclaration.BodyOnNextLineCASE" />
        <properties>
            <property name="lineLimit" value="130"/>
            <property name="absoluteLineLimit" value="135"/>
        </properties>
    </rule>
    <rule ref="Squiz.Arrays.ArrayDeclaration">
        <exclude name="Squiz.Arrays.ArrayDeclaration.ValueNotAligned" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.KeyNotAligned" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.DoubleArrowNotAligned" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.ValueNotAligned" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.CloseBraceNotAligned" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.ValueNoNewline" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.MultiLineNotAllowed" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.SingleLineNotAllowed" />
        <exclude name="Squiz.Functions.MultiLineFunctionDeclaration.NewlineBeforeOpenBrace" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.NoKeySpecified" />
        <exclude name="Squiz.Arrays.ArrayDeclaration.KeySpecified" />
    </rule>
    <rule ref="Squiz.PHP.CommentedOutCode"/>
    <rule ref="Squiz.PHP.DisallowSizeFunctionsInLoops"/>
    <rule ref="Squiz.PHP.DiscouragedFunctions">
        <properties>
            <property name="error" value="true"/>
        </properties>
    </rule>
    <rule ref="Squiz.PHP.Eval"/>
    <rule ref="Squiz.PHP.GlobalKeyword"/>
    <rule ref="Squiz.PHP.Heredoc"/>
    <rule ref="Squiz.PHP.LowercasePHPFunctions"/>
    <rule ref="Squiz.PHP.NonExecutableCode"/>
    <rule ref="Squiz.Scope.MemberVarScope"/>
    <rule ref="Squiz.Scope.MethodScope"/>
    <rule ref="Squiz.Scope.StaticThisUsage"/>
    <rule ref="Squiz.WhiteSpace.CastSpacing"/>
    <rule ref="Squiz.WhiteSpace.ControlStructureSpacing"/>
    <rule ref="Squiz.WhiteSpace.LanguageConstructSpacing"/>
    <rule ref="Squiz.WhiteSpace.LogicalOperatorSpacing"/>
    <rule ref="Squiz.WhiteSpace.ObjectOperatorSpacing">
        <properties>
            <property name="ignoreNewlines" value="true"/>
        </properties>
    </rule>
    <rule ref="Squiz.WhiteSpace.OperatorSpacing">
        <properties>
            <property name="ignoreNewlines" value="true"/>
        </properties>
    </rule>
    <rule ref="Squiz.WhiteSpace.PropertyLabelSpacing"/>
    <rule ref="Squiz.WhiteSpace.ScopeClosingBrace"/>
    <rule ref="Squiz.WhiteSpace.ScopeKeywordSpacing"/>
    <rule ref="Squiz.WhiteSpace.SemicolonSpacing"/>
    <rule ref="Zend.Files.ClosingTag"/>

    <file>app</file>
    <file>config</file>
    <file>public</file>
    <file>resources</file>
    <file>routes</file>
    <file>tests</file>

    <exclude-pattern>*/.phpstorm.meta.php</exclude-pattern>
    <exclude-pattern>*/_ide_helper.php</exclude-pattern>
    <exclude-pattern>*/database/*</exclude-pattern>
    <exclude-pattern>*/cache/*</exclude-pattern>
    <exclude-pattern>*/*.js</exclude-pattern>
    <exclude-pattern>*/*.css</exclude-pattern>
    <exclude-pattern>*/*.xml</exclude-pattern>
    <exclude-pattern>*/*.blade.php</exclude-pattern>
    <exclude-pattern>*/autoload.php</exclude-pattern>
    <exclude-pattern>*/storage/*</exclude-pattern>
    <exclude-pattern>*/docs/*</exclude-pattern>
    <exclude-pattern>*/vendor/*</exclude-pattern>
    <exclude-pattern>*/migrations/*</exclude-pattern>
    <exclude-pattern>*/config/*</exclude-pattern>
    <exclude-pattern>*/public/index.php</exclude-pattern>
    <exclude-pattern>*/*.blade.php</exclude-pattern>
    <exclude-pattern>*/Console/Kernel.php</exclude-pattern>
    <exclude-pattern>*/Exceptions/Handler.php</exclude-pattern>
    <exclude-pattern>*/Http/Kernel.php</exclude-pattern>
    <exclude-pattern>*/Providers/*</exclude-pattern>
    <exclude-pattern>*/resources/lang/*</exclude-pattern>

    <arg name="colors"/>
    <arg value="spv"/>
    <ini name="memory_limit" value="128M"/>
</ruleset>
```

###### th config file is taken from this repo: [https://github.com/fossbarrow/laravel-phpcs](https://github.com/fossbarrow/laravel-phpcs)

### 4. Integrate dev tools with git hooks

git hooks help you use spesific commands at the spesific time. you can integrate dev command with git hooks.

first you need to create a git repository in your project. use this command to do that:

```bash
$ git init
```

to integrate dev tools with git hooks you can use [Composer git hooks](https://github.com/BrainMaestro/composer-git-hooks) package.

before installation you should put these codesline of codes in the `composer.json` file of your laravel project.

```json
{
  // composer.json file

  "extra": {
    "hooks": {
      "pre-commit": ["./vendor/bin/php-cs-fixer fix .", "./vendor/bin/phpcbf", "./vendor/bin/phpcs"],

      "pre-push": ["./vendor/bin/phpunit"]
    }
  },

  "scripts": {
    "post-update-cmd": [
      // other scripts
      "./vendor/bin/cghooks update"
    ],
    "post-autoload-dump": [
      // other scripts
      "./vendor/bin/cghooks update"
    ]
  }
}
```

the `cghooks update` command register git hooks from composer.json to `.git` folder. you dont need to use this command manually because after using `composer install`, the `post-autoload-dump` will call this command. just install the package and it's done.

```bash
$ composer require --dev brainmaestro/composer-git-hooks
```

and now you can use `git commit` and the scripts will run automatically.