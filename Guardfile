guard :shell do
  watch(/src\/(main|test)\/java\/.+\.java/) do |m|
    title = "Test output"
    status = :failed

    msg = `mvn test -q`

    if $?.success?
      status = :success
    end

    n msg, title, status

    "-> #{msg}"
  end

  watch(/src\/(main|test)\/thrift\/.+\.thrift/) do |m|
    title = "Thrift Generation"
    status = :failed

    msg = `mvn generate-sources -q`

    if $?.success?
      status = :success
    end

    n msg, title, status

    "-> #{msg}"
  end
end
