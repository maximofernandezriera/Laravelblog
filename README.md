# Laravelblog

+++markdown

How To Create a Blog in Laravel

Author: Marcia Ramos
Published: July 26, 2023
Updated: August 6, 2024

Laravel is a PHP web application framework with an expressive, elegant syntax. It has a vast library of packages and handles much of the drudge work in programming, leaving you to focus on your creativity.

This tutorial describes how to use Laravel to build and publish a blog on Kinsta.

Prerequisites

To follow this tutorial, you’ll need:
	•	A web server (example: XAMPP).
	•	A GitHub, GitLab, or Bitbucket account.
	•	Laravel installed.
	•	An active MyKinsta account.

Note: Ensure the Apache and MySQL modules in XAMPP are running.

Quickstart With phpMyAdmin

	1.	With MySQL and Apache running, open phpMyAdmin by navigating to http://localhost/phpmyadmin/.

Create a New Laravel Project

	1.	Open your terminal.
	2.	Create a Laravel project called blog:

laravel new blog


	3.	Move to the project’s directory and check your setup with php artisan serve.

Configure the Database

	1.	In phpMyAdmin, create a new database named blog.
	2.	Update your .env file in the root of your project with the following:

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=blog
DB_USERNAME=your-db-username
DB_PASSWORD=your-db-password



Make the Posts Table

	1.	Run the following to create a model, migration, and controller:

php artisan make:model Post -mc


	2.	Open the generated migration file and define your schema in the up() method:

public function up() {
    Schema::create('posts', function (Blueprint $table) {
        $table->id();
        $table->string('title')->nullable();
        $table->text('description')->nullable();
        $table->string('image')->nullable();
        $table->timestamps();
    });
}


	3.	Run php artisan migrate to apply the migration.

How To Create Controllers

	1.	Install npm dependencies and start the Vite development server:

npm install
npm run dev


	2.	In PostController.php, add an index method:

public function index() {
    $post = "Laravel Tutorial Series One!";
    return view('posts.index', ['post' => $post]);
}
